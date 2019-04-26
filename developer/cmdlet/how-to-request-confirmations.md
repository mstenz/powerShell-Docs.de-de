---
title: 'Gewusst wie: Anfordern von Bestätigungen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f24f77d5-e224-4b62-b128-535e045d333e
caps.latest.revision: 9
ms.openlocfilehash: 19e96b612a8778d82cdbafb528a7ffeb01f15f99
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067840"
---
# <a name="how-to-request-confirmations"></a>Anfordern von Bestätigungen

In diesem Beispiel wird gezeigt, wie zum Aufrufen der [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) und [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) Methoden zum Anfordern von Bestätigungen aus der Benutzer, bevor eine Aktion ausgeführt wird.

> [!IMPORTANT]
> Weitere Informationen zur Behandlung dieser Anforderungen von Windows PowerShell finden Sie unter [Bestätigung anfordern](./requesting-confirmation-from-cmdlets.md).

## <a name="to-request-confirmation"></a>Eine Bestätigung anzufordern

1. Sicherstellen, dass die `SupportsShouldProcess` Parameter des Cmdlet-Attributs nastaven NA hodnotu `true`. (Für Funktionen ist dies ein Parameter des Attributs CmdletBinding.)

    ```csharp
    [Cmdlet(VerbsDiagnostic.Test, "RequestConfirmationTemplate1",
            SupportsShouldProcess = true)]
    ```

2. Hinzufügen einer `Force` Parameter, um Ihr Cmdlet, damit der Benutzer eine Bestätigungs-Anforderung überschreiben kann.

    ```csharp
    [Parameter()]
    public SwitchParameter Force
    {
      get { return force; }
      set { force = value; }
    }
    private bool force;
    ```

3. Hinzufügen einer `if` -Anweisung, die den Rückgabewert des verwendet die [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) Methode, um zu bestimmen, ob die [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) Methode wird aufgerufen.

4. Fügen Sie eine zweite `if` -Anweisung, den Rückgabewert von der [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) -Methode und der Wert des der `Force` Parameter, um zu bestimmen, ob der Vorgang sein soll ausgeführt.

## <a name="example"></a>Beispiel

Das folgende Codebeispiel zeigt die [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) und [System.Management.Automation.Cmdlet.ShouldContinue](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) Methoden aus aufgerufen werden, in der Überschreibung von der [System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode. Allerdings können Sie auch diese Methoden aus den anderen eingabeverarbeitungsmethoden aufrufen.

```csharp
protected override void ProcessRecord()
{
  if (ShouldProcess("ShouldProcess target"))
  {
    if (Force || ShouldContinue("", ""))
    {
      // Add code that performs the operation.
    }
  }
}
```

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)
