---
title: 'Gewusst wie: unterstützen von Transaktionen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4732e38c-b1a0-4de7-b6de-75dbde850488
caps.latest.revision: 8
ms.openlocfilehash: c5eea216efd8048aee5768c78c0b48617670f091
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857116"
---
# <a name="how-to-support-transactions"></a>Unterstützen von Transaktionen

Dieses Beispiel zeigt die grundlegende Codeelemente, die Unterstützung für Transaktionen an ein Cmdlet hinzufügen.

> [!IMPORTANT]
> Weitere Informationen zur Behandlung von Transaktionen in Windows PowerShell finden Sie unter [zu Transaktionen][about_Transactions].

## <a name="to-support-transactions"></a>Zur Unterstützung von Transaktionen

1. Wenn Sie das Cmdlet-Attribut deklarieren, geben Sie, dass das Cmdlet Transaktionen unterstützt.
   Wenn Sie das Cmdlet Transaktionen unterstützt, fügt Windows PowerShell die `UseTransaction` Parameter an das Cmdlet aus, wenn er ausgeführt wird.

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. In einem der eingabeverarbeitungsmethoden, Hinzufügen einer `if` Block, um zu bestimmen, ob eine Transaktion verfügbar ist.
   Wenn die `if` Anweisung löst in `true`, die Aktionen in dieser Anweisung können innerhalb des Kontexts der aktuellen Transaktion ausgeführt werden.

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a>Weitere Informationen

[Schreiben eines Windows PowerShell-Cmdlets](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
