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
ms.openlocfilehash: e5dc525a6c80ce135d6d68e12968613056d447e8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855186"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a>Aufrufen von Cmdlets und Skripts in einem Cmdlet

Ein Cmdlet kann andere Cmdlets und Skripts in der Eingabe Verarbeitungsmethode des-Cmdlets aufrufen. Dadurch können Sie Ihr Cmdlet die Funktionalität von vorhandenen Cmdlets und Skripts hinzuzufügen, ohne den Code umschreiben zu müssen.

## <a name="the-invoke-method"></a>Die Invoke-Methode

Alle Cmdlets können ein vorhandenes Cmdlet aufrufen, durch den Aufruf der [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) Methode innerhalb einer eingabeverarbeitungsmethode, z. B. [ System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), d. h. außer Kraft gesetzt, indem Sie das Cmdlet. Sie können jedoch nur die Cmdlets, die direkt vom abgeleitet sind Aufrufen der [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) Klasse. Sie können nicht aufgerufen werden ein Cmdlet, das von abgeleitet ist die [System.Management.Automation.Pscmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) Klasse.

Die [System.Management.Automation.Cmdlet.Invoke*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) Methode hat die folgenden Varianten.

[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) diese Variante der Cmdlet-Objekt aufruft, und gibt eine Auflistung von "T"-Type-Objekten.

[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) diese Variante ruft stattdessen das Cmdlet auf und gibt eine stark typisierte Emumerator. Diese Variante kann der Benutzer die Objekte in der Auflistung zu verwenden, um benutzerdefinierte Vorgänge auszuführen.

## <a name="examples"></a>Beispiele

|Beispiel|Beschreibung|
|-------------|-----------------|
|[Aufrufen des Cmdlets in einem Cmdlet](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|Dieses Beispiel zeigt, wie ein Cmdlet in ein anderes Cmdlet aufgerufen wird.|
|[Aufrufen von Skripts in einem Cmdlet](./how-to-invoke-scripts-within-a-cmdlet.md)|Dieses Beispiel zeigt, wie Sie ein Skript aufrufen, die an das Cmdlet aus, in ein anderes Cmdlet bereitgestellt werden.|

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
