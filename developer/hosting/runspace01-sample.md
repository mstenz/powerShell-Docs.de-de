---
title: Beispiel für Runspace01 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 42c1c59c-6da5-4cda-9562-e8059177fee1
caps.latest.revision: 11
ms.openlocfilehash: c33044fde4456513b5b07b998cc8db389b318e8e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855716"
---
# <a name="runspace01-sample"></a><span data-ttu-id="d0356-102">Runspace01-Beispiel</span><span class="sxs-lookup"><span data-stu-id="d0356-102">Runspace01 Sample</span></span>

<span data-ttu-id="d0356-103">Dieses Beispiel zeigt, wie Sie mit der [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) -Klasse zum Ausführen der [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet synchron.</span><span class="sxs-lookup"><span data-stu-id="d0356-103">This sample shows how to use the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchronously.</span></span> <span data-ttu-id="d0356-104">Die [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) -Cmdlet zurückgegeben ["System.Diagnostics.Process"](/dotnet/api/System.Diagnostics.Process) -Objekte für jeden Prozess auf dem lokalen Computer ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="d0356-104">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objects for each process running on the local computer.</span></span> <span data-ttu-id="d0356-105">Die Werte der [System.Diagnostics.Process.Processname\*](/dotnet/api/System.Diagnostics.Process.ProcessName) und [System.Diagnostics.Process.Handlecount\*](/dotnet/api/System.Diagnostics.Process.Handlecount) Eigenschaften klicken Sie dann aus der zurückgegebenen Objekte extrahiert und in einem Konsolenfenster angezeigt werden Fenster.</span><span class="sxs-lookup"><span data-stu-id="d0356-105">The values of the [System.Diagnostics.Process.Processname\*](/dotnet/api/System.Diagnostics.Process.ProcessName) and [System.Diagnostics.Process.Handlecount\*](/dotnet/api/System.Diagnostics.Process.Handlecount) properties are then extracted from the returned objects and displayed in a console window.</span></span>

## <a name="requirements"></a><span data-ttu-id="d0356-106">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="d0356-106">Requirements</span></span>

 <span data-ttu-id="d0356-107">Dieses Beispiel ist die Windows PowerShell 2.0 erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d0356-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="d0356-108">Veranschaulicht</span><span class="sxs-lookup"><span data-stu-id="d0356-108">Demonstrates</span></span>

- <span data-ttu-id="d0356-109">Erstellen einer [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) Objekt um einen Befehl auszuführen.</span><span class="sxs-lookup"><span data-stu-id="d0356-109">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to run a command.</span></span>

- <span data-ttu-id="d0356-110">Hinzufügen eines Befehls der Pipeline die [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) Objekt.</span><span class="sxs-lookup"><span data-stu-id="d0356-110">Adding a command to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="d0356-111">Den Befehl synchron ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="d0356-111">Running the command synchronously.</span></span>

- <span data-ttu-id="d0356-112">Mithilfe von [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) Objekte zum Extrahieren von Eigenschaften aus den Objekten, die vom Befehl zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="d0356-112">Using [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objects to extract properties from the objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="d0356-113">Beispiel</span><span class="sxs-lookup"><span data-stu-id="d0356-113">Example</span></span>

 <span data-ttu-id="d0356-114">In diesem Beispiel führt die [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) Cmdlet synchron auf dem standardmäßigen Runspace von Windows PowerShell bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="d0356-114">This sample runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchronously in the default runspace provided by Windows PowerShell.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Management.Automation;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace01
  {
    /// <summary>
    /// This sample uses the PowerShell class to execute
    /// the get-process cmdlet synchronously. The name and
    /// handlecount are then extracted from the PSObjects
    /// returned and displayed.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a PowerShell object to run a command.
    /// 2. Adding a command to the pipeline of the PowerShell object.
    /// 3. Running the command synchronously.
    /// 4. Using PSObject objects to extract properties from the objects
    ///    returned by the command.
    /// </remarks>
    private static void Main(string[] args)
    {
      // Create a PowerShell object. Creating this object takes care of
      // building all of the other data structures needed to run the command.
      using (PowerShell powershell = PowerShell.Create().AddCommand("get-process"))
      {
        Console.WriteLine("Process              HandleCount");
        Console.WriteLine("--------------------------------");

        // Invoke the command synchronously and display the
        // ProcessName and HandleCount properties of the
        // objects that are returned.
        foreach (PSObject result in powershell.Invoke())
        {
          Console.WriteLine(
                      "{0,-20} {1}",
                      result.Members["ProcessName"].Value,
                      result.Members["HandleCount"].Value);
        }
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="d0356-115">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d0356-115">See Also</span></span>
