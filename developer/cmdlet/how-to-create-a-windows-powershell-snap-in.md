---
title: 'Vorgehensweise: Erstellen Sie ein Windows PowerShell-Snap-in | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], examples
ms.assetid: 71bd9b2c-5f2e-4aa8-b5fe-08c956540d37
caps.latest.revision: 10
ms.openlocfilehash: 43199544dc02ccae4b61053c30d6ed36576adfcf
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067993"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a>Erstellen eines Windows PowerShell-Snap-Ins

Ein Windows PowerShell-Snap-in die bietet eines Mechanismus zum Registrieren von Sätze von Cmdlets und eine andere Windows PowerShell-Anbieter mit der Shell, daher zum Erweitern der Funktionalität der Shell aus. Ein Windows PowerShell-Snap-in kann die Cmdlets und Anbieter in einer einzelnen Assembly registrieren, oder sie können eine bestimmte Liste von Cmdlets und Anbieter.

-Snap-in Assemblys sollten in einem geschützten Verzeichnis installiert werden, wie sie mit anderen Betriebssystemen wäre. Andernfalls können böswillige Benutzer eine Assembly mit unsicherem Code ersetzen.

## <a name="windows-powershell-snap-in-classes"></a>Windows PowerShell-Snap-in Klassen

Alle Windows PowerShell-Snap-in Klassen leiten sich von der [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) oder [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) Klassen.

## <a name="examples"></a>Beispiele

[Schreiben ein Windows PowerShell-Snap-in](./writing-a-windows-powershell-snap-in.md): Dieses Beispiel zeigt, wie Sie ein Snap-in erstellen, die verwendet wird, um alle Cmdlets und Anbieter in einer Assembly zu registrieren.

[Schreiben ein benutzerdefiniertes Windows PowerShell-Snap-in](./writing-a-custom-windows-powershell-snap-in.md): Dieses Beispiel zeigt, wie Sie eine benutzerdefinierte-Snap-in erstellen, die verwendet wird, um einen bestimmten Satz von Cmdlets und Anbieter, die nicht existiert oder in einer einzelnen Assembly zu registrieren.

## <a name="see-also"></a>Weitere Informationen

[System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn)

[System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[Registrierung der Cmdlets](./registering-cmdlets.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
