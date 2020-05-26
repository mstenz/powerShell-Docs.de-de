---
title: Erstellen eines Windows PowerShell-Snap-Ins | Microsoft-Dokumentation
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
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83811329"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a>Erstellen eines Windows PowerShell-Snap-Ins

Ein Windows PowerShell-Snap-in bietet einen Mechanismus zum Registrieren von Cmdlets-Sätzen und eines anderen Windows PowerShell-Anbieters mit der Shell und erweitert so die Funktionalität der Shell. Mit einem Windows PowerShell-Snap-in können alle Cmdlets und Anbieter in einer einzelnen Assembly registriert werden, oder es kann eine bestimmte Liste von Cmdlets und Anbietern registriert werden.

Snap-in-Assemblys sollten in einem geschützten Verzeichnis installiert werden, genauso wie bei anderen Betriebssystemen. Andernfalls können böswillige Benutzer eine Assembly durch unsicheren Code ersetzen.

## <a name="windows-powershell-snap-in-classes"></a>Windows PowerShell-Snap-in-Klassen

Alle Windows PowerShell-Snap-in-Klassen werden von der [System. Management. Automation. PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) -Klasse oder der [System. Management. Automation. CustomPSSnapIn](/dotnet/api/System.Management.Automation.CustomPSSnapIn) -Klasse abgeleitet.

## <a name="examples"></a>Beispiele

[Schreiben eines Windows PowerShell-Snap-Ins](./writing-a-windows-powershell-snap-in.md): in diesem Beispiel wird gezeigt, wie ein Snap-in erstellt wird, das zum Registrieren aller Cmdlets und Anbieter in einer Assembly verwendet wird.

[Schreiben eines benutzerdefinierten Windows PowerShell-Snap-Ins](./writing-a-custom-windows-powershell-snap-in.md): in diesem Beispiel wird gezeigt, wie ein benutzerdefiniertes Snap-in erstellt wird, das zum Registrieren eines bestimmten Satzes von Cmdlets und Anbietern verwendet wird, die in einer einzelnen Assembly vorhanden sein könnten oder nicht.

## <a name="see-also"></a>Weitere Informationen

[System. Management. Automation. PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn)

[System. Management. Automation. CustomPSSnapIn](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[Registrieren von Cmdlets](./registering-cmdlets.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
