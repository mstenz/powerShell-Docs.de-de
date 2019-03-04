---
title: Meldungen zur benutzerbestätigung | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a886a26d-7730-4586-aeac-fd3f0bc60b88
caps.latest.revision: 8
ms.openlocfilehash: 75214a3fe4bc019836f75db19fb873bd081f200f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861416"
---
# <a name="confirmation-messages"></a>Bestätigungsmeldungen

Nachfolgend finden Sie verschiedene Bestätigungsnachrichten, die abhängig von der Varianten der angezeigt werden, können die [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) und [ System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) Methoden, die aufgerufen werden.

> [!IMPORTANT]
> Beispielcode, der zeigt, wie Sie Bestätigungen anfordern, finden Sie unter [wie Anforderung Bestätigungen](./how-to-request-confirmations.md).

## <a name="specifying-the-resource"></a>Angeben der Ressource

Sie können angeben, dass die Ressource, die durch Aufrufen von geändert werden, die [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) Methode. In diesem Fall geben Sie die Ressource mithilfe der `target` Parameter der Methode und der Vorgang wird von Windows PowerShell hinzugefügt. In der folgenden Meldung aus der Text "MyResource" ist die Ressource behandelt, und der Vorgang ist der Name des Befehls, der den Aufruf ausführt.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Wenn der Benutzer wählt **Ja** oder **Ja, alle** auf die Bestätigung anfordern (wie im folgenden Beispiel gezeigt), einen Aufruf der [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) Methode vorgenommen wird, die bewirkt, dass einer zweite bestätigungsmeldung angezeigt werden.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a>Angeben, den Betrieb und die Ressource

Sie können angeben, die Ressource, die geändert werden, und der Vorgang, der der Befehl führen Sie durch Aufrufen der [System.Management.Automation.Cmdlet.Shouldprocess%2A? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) Methode. In diesem Fall geben Sie die Ressource mithilfe der `target` Parameter und den Vorgang mit der `target` Parameter. In der folgenden Meldung aus der Text "MyResource" ist die Ressource behandelt, und "MyAction" ist der Vorgang ausgeführt werden.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Wenn der Benutzer auswählt **Ja** oder **Ja, alle** zur vorherigen Nachricht, einen Aufruf der [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) Methode vorgenommen wird, wodurch ein zweite bestätigungsmeldung angezeigt werden.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
