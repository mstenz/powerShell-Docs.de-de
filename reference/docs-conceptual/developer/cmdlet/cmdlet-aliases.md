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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369979"
---
# <a name="cmdlet-aliases"></a>Cmdlet-Aliase

Sie können Cmdlet-Aliase verwenden, um die Benutzer Darstellung des Cmdlets zu verbessern. Sie können-Aliase zu häufig verwendeten Cmdlets hinzufügen, um die Eingabe zu reduzieren und Aufgaben schneller auszuführen. Sie können integrierte Aliase in ihre Cmdlets einschließen, oder Benutzer können Ihre eigenen benutzerdefinierten Aliase definieren.

Beispielsweise verfügt das [Get-Command](/powershell/module/microsoft.powershell.core/get-command) -Cmdlet über einen integrierten `gcm`-Alias. Sie können Aliase auch zum Hinzufügen von Befehlsnamen aus anderen Sprachen verwenden, sodass Benutzer keine neuen Befehle erlernen müssen.

## <a name="alias-guidelines"></a>Alias Richtlinien

Befolgen Sie diese Richtlinien, wenn Sie integrierte Aliase für die Cmdlets erstellen:

- Bevor Sie Aliase zuweisen, starten Sie Windows PowerShell, und führen Sie dann das [Get-Alias-](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) Cmdlet aus, um die bereits verwendeten Aliase anzuzeigen.

- Fügen Sie ein Alias Präfix ein, das auf das Verb des Cmdlet-namens verweist, und ein Alias Suffix, das auf das Substantiv des Cmdlet-namens verweist. Der Alias für das Cmdlet "`Import-Module`" ist beispielsweise "ipmo". Eine Liste aller Verben und deren Aliase finden [Sie unter Cmdlet-Verben](./approved-verbs-for-windows-powershell-commands.md).

- Für Cmdlets, die über das gleiche Verb verfügen, müssen Sie dasselbe Alias Präfix einschließen. Beispielsweise wird für die Aliase für alle Windows PowerShell-Cmdlets, die das Verb "Get" im Namen aufweisen, das Präfix "g" verwendet.

- Verwenden Sie für Cmdlets mit demselben Substantiv dasselbe Alias Suffix. Beispielsweise wird für die Aliase für alle Windows PowerShell-Cmdlets, die das "Session"-Substantiv in Ihrem Namen aufweisen, das "sn"-Suffix verwendet.

- Verwenden Sie für Cmdlets, die Befehlen in anderen Sprachen entsprechen, den Namen des Befehls.

- Im Allgemeinen sollten Sie Aliase so kurz wie möglich machen. Stellen Sie sicher, dass der Alias mindestens ein unterschiedliches Zeichen für das Verb und ein eindeutiges Zeichen für das Substantiv aufweist. Fügen Sie nach Bedarf weitere Zeichen hinzu, um den Alias eindeutig zu machen.

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
