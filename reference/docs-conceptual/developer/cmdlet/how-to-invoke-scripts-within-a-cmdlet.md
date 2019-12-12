---
title: Aufrufen von Skripts in einem Cmdlet | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc0bc6ce-48a5-4d9c-927e-636bca743e9f
caps.latest.revision: 9
ms.openlocfilehash: 7dcb8bc20ab56225764854f9dc6fdfd858ed7451
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364409"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a><span data-ttu-id="37f16-102">Aufrufen von Skripts in einem Cmdlet</span><span class="sxs-lookup"><span data-stu-id="37f16-102">How to Invoke Scripts Within a Cmdlet</span></span>

<span data-ttu-id="37f16-103">Dieses Beispiel zeigt, wie ein Skript aufgerufen wird, das für ein Cmdlet bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="37f16-103">This example shows how to invoke a script that is supplied to a cmdlet.</span></span> <span data-ttu-id="37f16-104">Das Skript wird vom Cmdlet ausgeführt, und die Ergebnisse werden an das Cmdlet als Sammlung von [System. Management. Automation. psobject](/dotnet/api/System.Management.Automation.PSObject) -Objekten zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="37f16-104">The script is executed by the cmdlet, and its results are returned to the cmdlet as a collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects.</span></span>

## <a name="to-invoke-a-script-block"></a><span data-ttu-id="37f16-105">So rufen Sie einen Skriptblock auf</span><span class="sxs-lookup"><span data-stu-id="37f16-105">To invoke a script block</span></span>

1. <span data-ttu-id="37f16-106">Mit dem Befehl wird überprüft, ob ein Skriptblock für das Cmdlet bereitgestellt wurde.</span><span class="sxs-lookup"><span data-stu-id="37f16-106">The command verifies that a script block was supplied to the cmdlet.</span></span> <span data-ttu-id="37f16-107">Wenn ein Skriptblock angegeben wurde, ruft der Befehl den Skriptblock mit den erforderlichen Parametern auf.</span><span class="sxs-lookup"><span data-stu-id="37f16-107">If a script block was supplied, the command invokes the script block with its required parameters.</span></span>

    ```csharp
    if (script != null)
    {
      WriteDebug("Executing script block.");

      // Invoke the script block with the required arguments.
      Collection<PSObject> PSObjects =
                     script.Invoke(
                                   line,
                                   simpleMatch,
                                   caseSensitive
                                  );
    ```

2. <span data-ttu-id="37f16-108">Anschließend durchläuft das Skript die zurückgegebene Auflistung von [System. Management. Automation. psobject](/dotnet/api/System.Management.Automation.PSObject) -Objekten und führt die erforderlichen Vorgänge aus.</span><span class="sxs-lookup"><span data-stu-id="37f16-108">Then, the script iterates through the returned collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects and perform the necessary operations.</span></span>

    ```c
    foreach (PSObject psObject in psObjects)
    {
      if (LanguagePrimitives.IsTrue(psObject))
      {
        result = new MatchInfo();
        result.Line = line;
        result.IgnoreCase = !caseSensitive;

        break;
      }
    }

    ```

## <a name="see-also"></a><span data-ttu-id="37f16-109">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="37f16-109">See Also</span></span>

[<span data-ttu-id="37f16-110">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="37f16-110">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
