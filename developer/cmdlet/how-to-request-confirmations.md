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
ms.openlocfilehash: 8cfbcacf93733667ffba63a252c86518c0919b57
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863406"
---
# <a name="how-to-request-confirmations"></a>Anfordern von Bestätigungen

In diesem Beispiel wird gezeigt, wie zum Aufrufen der [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) und [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) Methoden zum Anfordern von Bestätigungen aus der Benutzer, bevor eine Aktion ausgeführt wird.

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

3. Hinzufügen einer `if` -Anweisung, die den Rückgabewert des verwendet die [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) Methode, um zu bestimmen, ob die [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) Methode wird aufgerufen.

4. Fügen Sie eine zweite `if` -Anweisung, den Rückgabewert von der [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) -Methode und der Wert des der `Force` Parameter, um zu bestimmen, ob der Vorgang sein soll ausgeführt.

## <a name="example"></a>Beispiel

Das folgende Codebeispiel zeigt die [System.Management.Automation.Cmdlet.Shouldprocess*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) und [System.Management.Automation.Cmdlet.Shouldcontinue*](/dotnet/api/System.Management.Automation.Cmdlet.ShouldContinue) Methoden werden aufgerufen, aus der außer Kraft setzen, der die [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) Methode. Allerdings können Sie auch diese Methoden aus den anderen eingabeverarbeitungsmethoden aufrufen.

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
