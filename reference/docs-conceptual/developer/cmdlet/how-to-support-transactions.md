---
title: Vorgehensweise beim unterstützen von Transaktionen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4732e38c-b1a0-4de7-b6de-75dbde850488
caps.latest.revision: 8
ms.openlocfilehash: c5eea216efd8048aee5768c78c0b48617670f091
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365539"
---
# <a name="how-to-support-transactions"></a>Unterstützen von Transaktionen

Dieses Beispiel zeigt die grundlegenden Code Elemente, die die Unterstützung für Transaktionen zu einem Cmdlet hinzufügen.

> [!IMPORTANT]
> Weitere Informationen zum Verarbeiten von Transaktionen in Windows PowerShell finden Sie unter [Informationen zu Transaktionen][about_Transactions].

## <a name="to-support-transactions"></a>So unterstützen Sie Transaktionen

1. Wenn Sie das Cmdlet-Attribut deklarieren, geben Sie an, dass das Cmdlet Transaktionen unterstützt.
   Wenn das Cmdlet Transaktionen unterstützt, fügt Windows PowerShell den `UseTransaction`-Parameter zum Cmdlet hinzu, wenn es ausgeführt wird.

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. Fügen Sie innerhalb einer der Eingabe Verarbeitungsmethoden einen `if`-Block hinzu, um zu bestimmen, ob eine Transaktion verfügbar ist.
   Wenn die `if`-Anweisung in `true`aufgelöst wird, können die Aktionen innerhalb dieser Anweisung innerhalb des Kontexts der aktuellen Transaktion ausgeführt werden.

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
