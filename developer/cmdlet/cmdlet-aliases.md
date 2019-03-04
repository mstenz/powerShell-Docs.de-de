---
title: Cmdlet-Aliase | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0d70864-33fb-49ce-8054-c41ba19fd554
caps.latest.revision: 11
ms.openlocfilehash: 32f45702cc0d28e6652ef61ebdbe085291013408
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860506"
---
# <a name="cmdlet-aliases"></a>Cmdlet-Aliase

Sie können Cmdlet-Aliase verwenden, um die Cmdlet-benutzerfreundlichkeit zu verbessern. Sie können Aliase für häufig verwendete-Cmdlets, Eingabe zu verringern und Abschließen von Aufgaben schnell erleichtern hinzufügen. Sie können die integrierten Aliase in Ihre Cmdlets einschließen, oder Benutzer können ihre eigenen benutzerdefinierten Aliasen definieren.

Z. B. die [Get-Command](/powershell/module/microsoft.powershell.core/get-command) Cmdlet verfügt über eine integrierte `gcm` Alias. Aliase können auch die Befehlsnamen aus anderen Sprachen hinzufügen, sodass Benutzer keine neuen Befehle zu erfahren.

## <a name="alias-guidelines"></a>Alias-Richtlinien

Beachten Sie Folgendes, wenn Sie die integrierten Aliase für Ihre Cmdlets erstellen:

- Bevor Sie den Aliasnamen zuweisen, starten Sie Windows PowerShell, und führen Sie die [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) Cmdlet, um die Aliase anzuzeigen, die bereits verwendet werden.

- Enthalten Sie ein Alias-Präfix, das verweist auf das Verb den Cmdlet-Namen und ein Alias-Suffix, die das Nomen der Cmdlet-Namen verweist. Z. B. der Alias für die `Import-Module` ist "Ipmo"-Cmdlet. Eine Liste der alle Verben und ihre Aliase, finden Sie unter [Cmdlet-Verbs](./approved-verbs-for-windows-powershell-commands.md).

- Cmdlets, die das gleiche Verb haben, enthalten Sie das gleiche Präfix für den Alias. Beispielsweise verwenden die Aliase für alle Windows PowerShell-Cmdlets, die das Verb "Get" in deren Namen das Präfix "g".

- Cmdlets, die dem gleichen Namen haben, enthalten Sie das gleiche Alias-Suffix. Beispielsweise verwenden die Aliase für alle Windows PowerShell-Cmdlets, die das Nomen "Session", deren Name das Suffix "sn".

- Verwenden Sie für Cmdlets, die von den Befehlen in anderen Sprachen entsprechen den Namen des Befehls.

- Im Allgemeinen stellen Sie Aliase so kurz wie möglich. Stellen Sie sicher, dass der Alias mindestens ein eigenständiges Zeichen für das Verb und ein eigenständiges Zeichen für die das Nomen verfügt. Fügen Sie mehr Zeichen, die nach Bedarf, um den alias eindeutig zu machen.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
