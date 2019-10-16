---
title: Aufrufen von Cmdlets und Skripts in einem Cmdlet | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: f20708ff41d9a6de90090997a875ba5371eccd74
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72364289"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a>Aufrufen von Cmdlets und Skripts in einem Cmdlet

Ein Cmdlet kann andere Cmdlets und Skripts in der Eingabe Verarbeitungsmethode des Cmdlets aufrufen. Dies ermöglicht es Ihnen, die Funktionalität vorhandener Cmdlets und Skripts zum Cmdlet hinzuzufügen, ohne den Code neu schreiben zu müssen.

## <a name="the-invoke-method"></a>Die Aufruf Methode

Alle Cmdlets können ein vorhandenes Cmdlet aufrufen, indem Sie die [System. Management. Automation. Cmdlet.](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) Call-Methode aus einer Eingabe Verarbeitungsmethode aufrufen, wie z [. b. System. Management. Automation. Cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), die von überschrieben wird. das-Cmdlet. Sie können jedoch nur die Cmdlets aufrufen, die direkt von der [System. Management. Automation. Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) -Klasse abgeleitet werden. Sie können kein Cmdlet aufrufen, das von der [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) -Klasse abgeleitet wird.

Die [System. Management. Automation. Cmdlet. aufrufen *](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) -Methode verfügt über die folgenden Varianten.

[System. Management. Automation. Cmdlet. aufrufen](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) diese Variante Ruft das Cmdlet-Objekt auf und gibt eine Auflistung von T-Objekten zurück.

[System. Management. Automation. Cmdlet. aufrufen](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) diese Variante Ruft das Cmdlet-Objekt auf und gibt einen stark typisierten emumerator zurück. Diese Variante ermöglicht dem Benutzer die Verwendung der Objekte in der Auflistung, um benutzerdefinierte Vorgänge auszuführen.

## <a name="examples"></a>Beispiele

|Beispiel|Description|
|-------------|-----------------|
|[Aufrufen von Cmdlets in einem Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|Dieses Beispiel zeigt, wie Sie ein Cmdlet in einem anderen Cmdlet aufrufen.|
|[Aufrufen von Skripts in einem Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md)|In diesem Beispiel wird gezeigt, wie ein Skript aufgerufen wird, das für das Cmdlet aus einem anderen Cmdlet bereitgestellt wird.|

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
