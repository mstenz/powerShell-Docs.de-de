---
title: Erstellen remote Runspaces | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 057a666f-731b-423d-9d80-7be6b1836244
caps.latest.revision: 5
ms.openlocfilehash: f6cc69df8afe64cea867f5d7f9a7d45753a54d6f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855806"
---
# <a name="creating-remote-runspaces"></a><span data-ttu-id="b124d-102">Erstellen von Remoterunspaces</span><span class="sxs-lookup"><span data-stu-id="b124d-102">Creating remote runspaces</span></span>

<span data-ttu-id="b124d-103">Windows PowerShell-Befehle, nehmen eine `ComputerName` Parameter kann auf alle Computer mit Windows PowerShell ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="b124d-103">Windows PowerShell commands that take a `ComputerName` parameter can be run on any computer that runs Windows PowerShell.</span></span> <span data-ttu-id="b124d-104">Zum Ausführen von Befehlen, die keinen akzeptieren einen `ComputerName` Parameter, Sie können verwenden Sie WS-Management, um einen Runspace konfigurieren Sie die Verbindung mit einem angegebenen Computer und führen Sie Befehle auf diesem Computer.</span><span class="sxs-lookup"><span data-stu-id="b124d-104">To run commands that do not take a `ComputerName` parameter, you can use WS-Management to configure a runspace that connects to a specified computer, and run commands on that computer.</span></span>

## <a name="using-a-wsmanconnection-to-create-a-remote-runspace"></a><span data-ttu-id="b124d-105">Verwenden eine WSManConnection einen Remoterunspace erstellen</span><span class="sxs-lookup"><span data-stu-id="b124d-105">Using a WSManConnection to create a remote runspace</span></span>

 <span data-ttu-id="b124d-106">Um einen Runspace erstellen, die mit einem Remotecomputer verbunden, erstellen Sie eine [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) Objekt.</span><span class="sxs-lookup"><span data-stu-id="b124d-106">To create a runspace that connects to a remote computer, you create a [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) object.</span></span> <span data-ttu-id="b124d-107">Geben Sie den Zielendpunkt für die Verbindung durch Festlegen der [System.Management.Automation.Runspaces.Wsmanconnectioninfo.Connectionuri\*](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ConnectionUri) -Eigenschaft des Objekts.</span><span class="sxs-lookup"><span data-stu-id="b124d-107">You specify the target endpoint for the connection by setting the [System.Management.Automation.Runspaces.Wsmanconnectioninfo.Connectionuri\*](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ConnectionUri) property of the object.</span></span> <span data-ttu-id="b124d-108">Sie erstellen dann einen Runspace durch Aufrufen der [System.Management.Automation.Runspaces.Runspacefactory.Createrunspace\*](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory.CreateRunspace) -Methode, Angeben der [System.Management.Automation.Runspaces.Wsmanconnectioninfo ](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) -Objekts entsprechend der `connectionInfo` Parameter.</span><span class="sxs-lookup"><span data-stu-id="b124d-108">You then create a runspace by calling the [System.Management.Automation.Runspaces.Runspacefactory.Createrunspace\*](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory.CreateRunspace) method, specifying the [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) object as the `connectionInfo` parameter.</span></span>

 <span data-ttu-id="b124d-109">Das folgende Beispiel zeigt, wie Sie einen Runspace erstellen, der mit einem Remotecomputer verbunden.</span><span class="sxs-lookup"><span data-stu-id="b124d-109">The following example shows how to create a runspace that connects to a remote computer.</span></span> <span data-ttu-id="b124d-110">Im Beispiel `RemoteComputerUri` dient als Platzhalter für den tatsächlichen URI von einem Remotecomputer befindet.</span><span class="sxs-lookup"><span data-stu-id="b124d-110">In the example, `RemoteComputerUri` is used as a placeholder for the actual URI of a remote computer.</span></span>

```csharp
namespace Samples
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;            // Windows PowerShell namespace.
  using System.Management.Automation.Runspaces;  // Windows PowerShell namespace.

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class RemoteRunspace02
  {
    /// <summary>
    /// This sample shows how to create a remote runspace that
    /// runs commands on the local computer.
    /// </summary>
    /// <param name="args">Parameter not used.</param>
    private static void Main(string[] args)
    {
      // Create a WSManConnectionInfo object using the default constructor
      // to connect to the "localHost". The WSManConnectionInfo object can
      // also be used to specify connections to remote computers.
      WSManConnectionInfo connectionInfo = new WSManConnectionInfo();

      // Set the OperationTimeout property and OpenTimeout properties.
      // The OperationTimeout property is used to tell Windows PowerShell
      // how long to wait (in milliseconds) before timing out for an
      // operation. The OpenTimeout property is used to tell Windows
      // PowerShell how long to wait (in milliseconds) before timing out
      // while establishing a remote connection.
      connectionInfo.OperationTimeout = 4 * 60 * 1000; // 4 minutes.
      connectionInfo.OpenTimeout = 1 * 60 * 1000; // 1 minute.

      // Create a remote runspace using the connection information.
      //using (Runspace remoteRunspace = RunspaceFactory.CreateRunspace())
      using (Runspace remoteRunspace = RunspaceFactory.CreateRunspace(connectionInfo))
      {
        // Establish the connection by calling the Open() method to open the runspace.
        // The OpenTimeout value set previously will be applied while establishing
        // the connection. Establishing a remote connection involves sending and
        // receiving some data, so the OperationTimeout will also play a role in this process.
          remoteRunspace.Open();

        // Create a PowerShell object to run commands in the remote runspace.
        using (PowerShell powershell = PowerShell.Create())
        {
          powershell.Runspace = remoteRunspace;
          powershell.AddCommand("get-process");
          powershell.Invoke();

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

        // Close the connection. Call the Close() method to close the remote
        // runspace. The Dispose() method (called by using primitive) will call
        // the Close() method if it is not already called.
        remoteRunspace.Close();
      }
    }
  }
}
```
