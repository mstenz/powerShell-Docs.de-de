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
# <a name="how-to-support-transactions"></a><span data-ttu-id="aa8a1-102">Unterstützen von Transaktionen</span><span class="sxs-lookup"><span data-stu-id="aa8a1-102">How to Support Transactions</span></span>

<span data-ttu-id="aa8a1-103">Dieses Beispiel zeigt die grundlegende Codeelemente, die Unterstützung für Transaktionen an ein Cmdlet hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="aa8a1-103">This example shows the basic code elements that add support for transactions to a cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aa8a1-104">Weitere Informationen zur Behandlung von Transaktionen in Windows PowerShell finden Sie unter [zu Transaktionen][about_Transactions].</span><span class="sxs-lookup"><span data-stu-id="aa8a1-104">For more information about how Windows PowerShell handles transactions, see [About Transactions][about_Transactions].</span></span>

## <a name="to-support-transactions"></a><span data-ttu-id="aa8a1-105">Zur Unterstützung von Transaktionen</span><span class="sxs-lookup"><span data-stu-id="aa8a1-105">To support transactions</span></span>

1. <span data-ttu-id="aa8a1-106">Wenn Sie das Cmdlet-Attribut deklarieren, geben Sie, dass das Cmdlet Transaktionen unterstützt.</span><span class="sxs-lookup"><span data-stu-id="aa8a1-106">When you declare the Cmdlet attribute, specify that the cmdlet supports transactions.</span></span>
   <span data-ttu-id="aa8a1-107">Wenn Sie das Cmdlet Transaktionen unterstützt, fügt Windows PowerShell die `UseTransaction` Parameter an das Cmdlet aus, wenn er ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="aa8a1-107">When the cmdlet supports transactions, Windows PowerShell adds the `UseTransaction` parameter to the cmdlet when it is run.</span></span>

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. <span data-ttu-id="aa8a1-108">In einem der eingabeverarbeitungsmethoden, Hinzufügen einer `if` Block, um zu bestimmen, ob eine Transaktion verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="aa8a1-108">Within one of the input processing methods, add an `if` block to determine if a transaction is available.</span></span>
   <span data-ttu-id="aa8a1-109">Wenn die `if` Anweisung löst in `true`, die Aktionen in dieser Anweisung können innerhalb des Kontexts der aktuellen Transaktion ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="aa8a1-109">If the `if` statement resolves to `true`, the actions within this statement can be performed within the context of the current transaction.</span></span>

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a><span data-ttu-id="aa8a1-110">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="aa8a1-110">See Also</span></span>

[<span data-ttu-id="aa8a1-111">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="aa8a1-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
