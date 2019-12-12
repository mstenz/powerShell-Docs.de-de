---
title: Bestätigungsmeldungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a886a26d-7730-4586-aeac-fd3f0bc60b88
caps.latest.revision: 8
ms.openlocfilehash: 229725b5b9f1f0082592dcebe11564fd2f630ce1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365729"
---
# <a name="confirmation-messages"></a>Bestätigungsmeldungen

Im folgenden finden Sie unterschiedliche Bestätigungsmeldungen, die je nach den Varianten der Methoden " [System. Management. Automation. Cmdlet. Schulter dprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) " und " [System. Management. Automation. Cmdlet. schuldcontinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) " angezeigt werden können.

> [!IMPORTANT]
> Beispielcode, der zeigt, wie Bestätigungen angefordert werden, finden Sie unter [anfordern von Bestätigungen](./how-to-request-confirmations.md).

## <a name="specifying-the-resource"></a>Angeben der Ressource

Sie können die zu ändernde Ressource angeben, indem Sie das [System. Management. Automation. Cmdlet aufrufen. Displayproperty = FullName](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) -Methode. In diesem Fall stellen Sie die Ressource mithilfe des `target`-Parameters der-Methode bereit, und der Vorgang wird von Windows PowerShell hinzugefügt. In der folgenden Meldung ist der Text "MyResource" die Ressource, auf die reagiert wird, und der Vorgang ist der Name des Befehls, der den-Vorgang ausführt.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Wenn der Benutzer für die Bestätigungs Anforderung **Ja** oder **Ja** (wie im folgenden Beispiel gezeigt) auswählt, wird ein [System. Management. Automation. Cmdlet. ermdcontinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) -Methode aufgerufen, wodurch eine zweite Bestätigungsmeldung angezeigt wird.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "Test-RequestConfirmationTemplate1" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"): y

Confirm
Continue with this operation?
[Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"):
```

## <a name="specifying-the-operation-and-resource"></a>Angeben des Vorgangs und der Ressource

Sie können die zu ändernde Ressource und den von dem Befehl auszuführenden Vorgang angeben, indem Sie das [System. Management. Automation. Cmdlet. tiondprocess% 2a aufrufen? Displayproperty = FullName](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess?view=powershellsdk-1.1.0) -Methode. In diesem Fall geben Sie die Ressource mit dem `target`-Parameter und dem-Vorgang mithilfe des `target`-Parameters an. In der folgenden Meldung ist der Text "MyResource" die Ressource, die ausgeführt wird, und "myaction" ist der Vorgang, der ausgeführt werden soll.

```output
Confirm
Are you sure you want to perform this action?
Performing operation "MyAction" on Target "MyResource".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Wenn der Benutzer für die vorherige Nachricht **Ja** oder **Ja** ausgewählt hat, wird ein Rückruf der [System. Management. Automation. Cmdlet. ermdcontinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) -Methode durchgeführt, wodurch eine zweite Bestätigungsmeldung angezeigt wird.

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
