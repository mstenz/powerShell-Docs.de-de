---
title: Erstellen von Remoterunspaces | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 057a666f-731b-423d-9d80-7be6b1836244
caps.latest.revision: 5
ms.openlocfilehash: 964320108d7aff24d59905028fb976e0f75642e7
ms.sourcegitcommit: 08e9ed4bc9bffc7af82b3130e74ec7763db74e4f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/13/2020
ms.locfileid: "83382625"
---
# <a name="creating-remote-runspaces"></a><span data-ttu-id="29871-102">Erstellen von Remoterunspaces</span><span class="sxs-lookup"><span data-stu-id="29871-102">Creating remote runspaces</span></span>

<span data-ttu-id="29871-103">PowerShell-Befehle, die einen **Computername** -Parameter annehmen, können auf jedem Computer ausgeführt werden, auf dem PowerShell ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="29871-103">PowerShell commands that take a **ComputerName** parameter can be run on any computer that runs PowerShell.</span></span> <span data-ttu-id="29871-104">Zum Ausführen von Befehlen, die keinen **Computername** -Parameter verwenden, können Sie die WS-Verwaltung verwenden, um einen Runspace zu konfigurieren, der eine Verbindung mit einem angegebenen Computer herstellt, und Befehle auf diesem Computer auszuführen.</span><span class="sxs-lookup"><span data-stu-id="29871-104">To run commands that don't take a **ComputerName** parameter, you can use WS-Management to configure a runspace that connects to a specified computer, and run commands on that computer.</span></span>

## <a name="using-a-wsmanconnection-to-create-a-remote-runspace"></a><span data-ttu-id="29871-105">Verwenden von wsmanconnection zum Erstellen eines Remoterunspace</span><span class="sxs-lookup"><span data-stu-id="29871-105">Using a WSManConnection to create a remote runspace</span></span>

 <span data-ttu-id="29871-106">Um einen Runspace zu erstellen, der eine Verbindung mit einem Remote Computer herstellt, erstellen Sie ein [System. Management. Automation. Runspaces. wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) -Objekt.</span><span class="sxs-lookup"><span data-stu-id="29871-106">To create a runspace that connects to a remote computer, you create a [System.Management.Automation.Runspaces.WSManConnectionInfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) object.</span></span> <span data-ttu-id="29871-107">Sie geben den Ziel Endpunkt für die Verbindung an, indem Sie die [System. Management. Automation. Runspaces. wsmanconnectioninfo. ConnectionUri](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ConnectionUri) -Eigenschaft des-Objekts festlegen.</span><span class="sxs-lookup"><span data-stu-id="29871-107">You specify the target endpoint for the connection by setting the [System.Management.Automation.Runspaces.WSManConnectionInfo.ConnectionUri](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ConnectionUri) property of the object.</span></span> <span data-ttu-id="29871-108">Anschließend erstellen Sie einen Runspace, indem Sie die [System. Management. Automation. Runspaces. runspacefactory. createrunspace](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory.CreateRunspace) -Methode aufrufen und das [System. Management. Automation. Runspaces. wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) -Objekt als `connectionInfo` Parameter angeben.</span><span class="sxs-lookup"><span data-stu-id="29871-108">You then create a runspace by calling the [System.Management.Automation.Runspaces.RunspaceFactory.CreateRunspace](/dotnet/api/System.Management.Automation.Runspaces.RunspaceFactory.CreateRunspace) method, specifying the [System.Management.Automation.Runspaces.WSManConnectionInfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo) object as the `connectionInfo` parameter.</span></span>

 <span data-ttu-id="29871-109">Im folgenden Beispiel wird gezeigt, wie ein Runspace erstellt wird, der eine Verbindung mit einem Remote Computer herstellt.</span><span class="sxs-lookup"><span data-stu-id="29871-109">The following example shows how to create a runspace that connects to a remote computer.</span></span> <span data-ttu-id="29871-110">Im Beispiel `RemoteComputerUri` wird als Platzhalter für den tatsächlichen URI eines Remote Computers verwendet.</span><span class="sxs-lookup"><span data-stu-id="29871-110">In the example, `RemoteComputerUri` is used as a placeholder for the actual URI of a remote computer.</span></span>

```csharp
namespace Samples
{
  using System;
  using System.Collections.ObjectModel;
  using System.Management.Automation;            // PowerShell namespace.
  using System.Management.Automation.Runspaces;  // PowerShell namespace.

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
      Uri RemoteComputerUri = new Uri("http://Server01:5985/WSMAN");
      WSManConnectionInfo connectionInfo = new WSManConnectionInfo(RemoteComputerUri);

      // Set the OperationTimeout property and OpenTimeout properties.
      // The OperationTimeout property is used to tell PowerShell
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
