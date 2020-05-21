---
title: Runspace06-Beispiel | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 471c85f3-9287-45c2-b4bc-833caa1b7634
caps.latest.revision: 8
ms.openlocfilehash: 49a938a5acd7817476b299deea465771b6a94985
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83563667"
---
# <a name="runspace06-sample"></a><span data-ttu-id="35b89-102">Runspace06-Beispiel</span><span class="sxs-lookup"><span data-stu-id="35b89-102">Runspace06 Sample</span></span>

<span data-ttu-id="35b89-103">In diesem Beispiel wird gezeigt, wie ein Modul einem [System. Management. Automation. Runspaces. initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -Objekt hinzugefügt wird, damit das Modul beim Öffnen des Runspace geladen wird.</span><span class="sxs-lookup"><span data-stu-id="35b89-103">This sample shows how to add a module to an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object so that the module is loaded when the runspace is opened.</span></span> <span data-ttu-id="35b89-104">Das Modul stellt ein Get-proc-Cmdlet bereit (definiert durch das [GetProcessSample02-Beispiel](../cmdlet/getprocesssample02-sample.md)), das synchron mithilfe eines [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -Objekts ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="35b89-104">The module provides a Get-Proc cmdlet (defined by the [GetProcessSample02 Sample](../cmdlet/getprocesssample02-sample.md)) that is run synchronously by using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

## <a name="requirements"></a><span data-ttu-id="35b89-105">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="35b89-105">Requirements</span></span>

<span data-ttu-id="35b89-106">Dieses Beispiel erfordert Windows PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="35b89-106">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="35b89-107">Zeigt</span><span class="sxs-lookup"><span data-stu-id="35b89-107">Demonstrates</span></span>

<span data-ttu-id="35b89-108">In diesem Beispiel wird Folgendes veranschaulicht:</span><span class="sxs-lookup"><span data-stu-id="35b89-108">This sample demonstrates the following.</span></span>

- <span data-ttu-id="35b89-109">Ein [System. Management. Automation. Runspaces. initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -Objekt wird erstellt.</span><span class="sxs-lookup"><span data-stu-id="35b89-109">Creating an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="35b89-110">Hinzufügen des Moduls zum [System. Management. Automation. Runspaces. initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -Objekt.</span><span class="sxs-lookup"><span data-stu-id="35b89-110">Adding the module to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="35b89-111">Erstellen eines [System. Management. Automation. Runspaces. Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) -Objekts, das das [System. Management. Automation. Runspaces. initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -Objekt verwendet.</span><span class="sxs-lookup"><span data-stu-id="35b89-111">Creating a [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object that uses the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="35b89-112">Erstellen eines [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -Objekts, das den Runspace verwendet.</span><span class="sxs-lookup"><span data-stu-id="35b89-112">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the runspace.</span></span>

- <span data-ttu-id="35b89-113">Das Get-proc-Cmdlet des Moduls wird der Pipeline des [System. Management. Automation. PowerShell](/dotnet/api/system.management.automation.powershell) -Objekts hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="35b89-113">Adding the module's get-proc cmdlet to the pipeline of the [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object.</span></span>

- <span data-ttu-id="35b89-114">Synchrones Ausführen des Befehls.</span><span class="sxs-lookup"><span data-stu-id="35b89-114">Running the command synchronously.</span></span>

- <span data-ttu-id="35b89-115">Extrahieren von Eigenschaften aus den [System. Management. Automation. psobject](/dotnet/api/System.Management.Automation.PSObject) -Objekten, die vom Befehl zurückgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="35b89-115">Extracting properties from the [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects returned by the command.</span></span>

## <a name="example"></a><span data-ttu-id="35b89-116">Beispiel</span><span class="sxs-lookup"><span data-stu-id="35b89-116">Example</span></span>

<span data-ttu-id="35b89-117">In diesem Beispiel wird ein Runspace erstellt, der ein [System. Management. Automation. Runspaces. initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -Objekt verwendet, um die Elemente zu definieren, die beim Öffnen des Runspace verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="35b89-117">This sample creates a runspace that uses an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object to define the elements that are available when the runspace is opened.</span></span> <span data-ttu-id="35b89-118">In diesem Beispiel wird ein Modul, das ein Get-proc-Cmdlet definiert, dem anfänglichen Sitzungszustand hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="35b89-118">In this sample, a module that defines a Get-Proc cmdlet is added to the initial session state.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace06
  {
    /// <summary>
    /// This sample shows how to define an initial session state that is
    /// used when creating a runspace. The sample invokes a command from
    /// a binary module that is loaded by the initial session state.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    /// <remarks>
    /// This sample assumes that user has coppied the GetProcessSample02.dll
    /// that is produced by the GetProcessSample02 sample to the current
    /// directory.
    /// This sample demonstrates the following:
    /// 1. Creating a default initial session state.
    /// 2. Adding a module to the initial session state.
    /// 3. Creating a runspace that uses the initial session state.
    /// 4. Creating a PowerShell object that uses the runspace.
    /// 5. Adding the module's get-proc cmdlet to the PowerShell object.
    /// 6. Running the command synchronously.
    /// 7. Using PSObject objects to extract and display properties from
    ///    the objects returned by the cmdlet.
    /// </remarks>
    private static void Main(string[] args)
    {
        // Create the default initial session state and add the module.
      InitialSessionState iss = InitialSessionState.CreateDefault();
      iss.ImportPSModule(new string[] { @".\GetProcessSample02.dll" });

      // Create a runspace. Notice that no PSHost object is supplied to the
      // CreateRunspace method so the default host is used. See the Host
      // samples for more information on creating your own custom host.
      using (Runspace myRunSpace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunSpace.Open();

        // Create a PowerShell object.
        using (PowerShell powershell = PowerShell.Create())
        {
          // Add the cmdlet and specify the runspace.
          powershell.AddCommand(@"GetProcessSample02\get-proc");
          powershell.Runspace = myRunSpace;

          Collection<PSObject> results = powershell.Invoke();

          Console.WriteLine("Process              HandleCount");
          Console.WriteLine("--------------------------------");

          // Display the results.
          foreach (PSObject result in results)
          {
            Console.WriteLine(
                              "{0,-20} {1}",
                              result.Members["ProcessName"].Value,
                              result.Members["HandleCount"].Value);
          }
        }

        // Close the runspace to release any resources.
        myRunSpace.Close();
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="35b89-119">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="35b89-119">See Also</span></span>

[<span data-ttu-id="35b89-120">Schreiben einer Windows PowerShell-Hostanwendung</span><span class="sxs-lookup"><span data-stu-id="35b89-120">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)
