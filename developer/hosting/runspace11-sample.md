---
title: Beispiel für Runspace11 | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c90d268-730b-4e73-9dfd-5f288c27aed0
caps.latest.revision: 8
ms.openlocfilehash: 74d7c9e9cb0d7ce829635e6aff994473e09e7479
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057211"
---
# <a name="runspace11-sample"></a><span data-ttu-id="50dca-102">Runspace11-Beispiel</span><span class="sxs-lookup"><span data-stu-id="50dca-102">Runspace11 Sample</span></span>

<span data-ttu-id="50dca-103">Dieses Beispiel zeigt, wie Sie mit der [System.Management.Automation.Proxycommand](/dotnet/api/System.Management.Automation.ProxyCommand) Klasse, um einen Proxybefehl zu erstellen, die ein vorhandenes Cmdlet aufruft, aber der Satz der verfügbaren Parameter einschränkt.</span><span class="sxs-lookup"><span data-stu-id="50dca-103">This sample shows how to use the [System.Management.Automation.Proxycommand](/dotnet/api/System.Management.Automation.ProxyCommand) class to create a proxy command that calls an existing cmdlet, but restricts the set of available parameters.</span></span> <span data-ttu-id="50dca-104">Der Proxybefehl wird anschließend zu einem anfänglichen Sitzungsstatus hinzugefügt, der dazu verwendet wird, einen eingeschränkten Runspace zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="50dca-104">The proxy command is then added to an initial session state that is used to create a constrained runspace.</span></span> <span data-ttu-id="50dca-105">Dies bedeutet, dass der Benutzer nur über den Proxybefehl auf die Funktionalität des Cmdlets zugreifen kann.</span><span class="sxs-lookup"><span data-stu-id="50dca-105">This means that the user can access the functionality of the cmdlet only through the proxy command.</span></span>

## <a name="requirements"></a><span data-ttu-id="50dca-106">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="50dca-106">Requirements</span></span>

<span data-ttu-id="50dca-107">Dieses Beispiel ist die Windows PowerShell 2.0 erforderlich.</span><span class="sxs-lookup"><span data-stu-id="50dca-107">This sample requires Windows PowerShell 2.0.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="50dca-108">Veranschaulicht</span><span class="sxs-lookup"><span data-stu-id="50dca-108">Demonstrates</span></span>

<span data-ttu-id="50dca-109">Dieses Beispiel veranschaulicht die folgenden.</span><span class="sxs-lookup"><span data-stu-id="50dca-109">This sample demonstrates the following.</span></span>

- <span data-ttu-id="50dca-110">Erstellen einer [System.Management.Automation.Commandmetadata](/dotnet/api/System.Management.Automation.CommandMetadata) Objekt, das die Metadaten der ein vorhandenes Cmdlet beschreibt.</span><span class="sxs-lookup"><span data-stu-id="50dca-110">Creating a [System.Management.Automation.Commandmetadata](/dotnet/api/System.Management.Automation.CommandMetadata) object that describes the metadata of an existing cmdlet.</span></span>

- <span data-ttu-id="50dca-111">Erstellen einer [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) Objekt.</span><span class="sxs-lookup"><span data-stu-id="50dca-111">Creating an [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object.</span></span>

- <span data-ttu-id="50dca-112">Ändern die Cmdlet-Metadaten, um einen Parameter des Cmdlets zu entfernen.</span><span class="sxs-lookup"><span data-stu-id="50dca-112">Modifying the cmdlet metadata to remove a parameter of the cmdlet.</span></span>

- <span data-ttu-id="50dca-113">Das Cmdlet zum Hinzufügen der [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) -Objekt, und machen das Cmdlet private.</span><span class="sxs-lookup"><span data-stu-id="50dca-113">Adding the cmdlet to the [System.Management.Automation.Runspaces.Initialsessionstate](/dotnet/api/System.Management.Automation.Runspaces.InitialSessionState) object and making the cmdlet private.</span></span>

- <span data-ttu-id="50dca-114">Erstellen eine Proxyfunktion, die das vorhandene Cmdlet aufruft, macht aber nur einen eingeschränkten Satz von Parametern.</span><span class="sxs-lookup"><span data-stu-id="50dca-114">Creating a proxy function that calls the existing cmdlet, but exposes only a restricted set of parameters.</span></span>

- <span data-ttu-id="50dca-115">Die Proxyfunktion und den anfänglichen Sitzungsstatus hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="50dca-115">Adding the proxy function to the initial session state.</span></span>

- <span data-ttu-id="50dca-116">Erstellen einer [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) , verwendet der [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) Objekt.</span><span class="sxs-lookup"><span data-stu-id="50dca-116">Creating a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object that uses the [System.Management.Automation.Runspaces.Runspace](/dotnet/api/System.Management.Automation.Runspaces.Runspace) object.</span></span>

- <span data-ttu-id="50dca-117">Aufrufen der private-Cmdlet und die Proxy-Funktion mit einem [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) Objekt, das den eingeschränkten Runspace zu veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="50dca-117">Calling the private cmdlet and the proxy function using a [System.Management.Automation.Powershell](/dotnet/api/system.management.automation.powershell) object to demonstrate the constrained runspace.</span></span>

## <a name="example"></a><span data-ttu-id="50dca-118">Beispiel</span><span class="sxs-lookup"><span data-stu-id="50dca-118">Example</span></span>

<span data-ttu-id="50dca-119">Dadurch wird einen Proxybefehl für ein private-Cmdlet zum veranschaulichen von eines eingeschränkten Runspaces erstellt.</span><span class="sxs-lookup"><span data-stu-id="50dca-119">This creates a proxy command for a private cmdlet to demonstrate a constrained runspace.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Runspaces
{
  using System;
  using System.Collections.Generic;
  using System.Diagnostics;
  using System.Management.Automation;
  using System.Management.Automation.Runspaces;
  using PowerShell = System.Management.Automation.PowerShell;

  #region GetProcCommand

  /// <summary>
  /// This class implements the get-proc cmdlet. It has been copied
  /// verbatim from the GetProcessSample02.cs sample.
  /// </summary>
  [Cmdlet(VerbsCommon.Get, "Proc")]
  public class GetProcCommand : Cmdlet
  {
    #region Parameters

    /// <summary>
    /// The names of the processes to act on.
    /// </summary>
    private string[] processNames;

    /// <summary>
    /// Gets or sets the list of process names on which
    /// the Get-Proc cmdlet will work.
    /// </summary>
    [Parameter(Position = 0)]
    [ValidateNotNullOrEmpty]
    public string[] Name
    {
      get { return this.processNames; }
      set { this.processNames = value; }
    }

    #endregion Parameters

    #region Cmdlet Overrides

    /// <summary>
    /// The ProcessRecord method calls the Process.GetProcesses
    /// method to retrieve the processes specified by the Name
    /// parameter. Then, the WriteObject method writes the
    /// associated processes to the pipeline.
    /// </summary>
    protected override void ProcessRecord()
    {
      // If no process names are passed to the cmdlet, get all
      // processes.
      if (this.processNames == null)
      {
        WriteObject(Process.GetProcesses(), true);
      }
      else
      {
        // If process names are passed to cmdlet, get and write
        // the associated processes.
        foreach (string name in this.processNames)
        {
          WriteObject(Process.GetProcessesByName(name), true);
        }
      } // if (processNames...
    } // ProcessRecord

    #endregion Cmdlet Overrides
  } // GetProcCommand

  #endregion GetProcCommand

  /// <summary>
  /// This class contains the Main entry point for this host application.
  /// </summary>
  internal class Runspace11
  {
    /// <summary>
    /// This shows how to use the ProxyCommand class to create a proxy
    /// command that calls an existing cmdlet, but restricts the set of
    /// available parameters. The proxy command is then added to an initial
    /// session state that is used to create a constrained runspace. This
    /// means that the user can access the cmdlet only through the proxy
    /// command.
    /// </summary>
    /// <remarks>
    /// This sample demonstrates the following:
    /// 1. Creating a CommandMetadata object that describes the metadata of an
    ///    existing cmdlet.
    /// 2. Modifying the cmdlet metadata to remove a parameter of the cmdlet.
    /// 3. Adding the cmdlet to an initial session state and making it private.
    /// 4. Creating a proxy function that calls the existing cmdlet, but exposes
    ///    only a restricted set of parameters.
    /// 6. Adding the proxy function to the initial session state.
    /// 7. Calling the private cmdlet and the proxy function to demonstrate the
    ///    constrained runspace.
    /// </remarks>
    private static void Main()
    {
      // Create a default initial session state. The default initial session state
      // includes all the elements that are provided by Windows PowerShell.
      InitialSessionState iss = InitialSessionState.CreateDefault();

      // Add the get-proc cmdlet to the initial session state.
      SessionStateCmdletEntry cmdletEntry = new SessionStateCmdletEntry("get-proc", typeof(GetProcCommand), null);
      iss.Commands.Add(cmdletEntry);

      // Make the cmdlet private so that it is not accessible.
      cmdletEntry.Visibility = SessionStateEntryVisibility.Private;

      // Set the language mode of the initial session state to NoLanguage to
      //prevent users from using language features. Only the invocation of
      // public commands is allowed.
      iss.LanguageMode = PSLanguageMode.NoLanguage;

      // Create the proxy command using cmdlet metadata to expose the
      // get-proc cmdlet.
      CommandMetadata cmdletMetadata = new CommandMetadata(typeof(GetProcCommand));

      // Remove one of the parameters from the command metadata.
      cmdletMetadata.Parameters.Remove("Name");

      // Generate the body of a proxy function that calls the original cmdlet,
      // but does not have the removed parameter.
      string bodyOfProxyFunction = ProxyCommand.Create(cmdletMetadata);

      // Add the proxy function to the initial session state. The name of the proxy
      // function can be the same as the name of the cmdlet, but to clearly
      // demonstrate that the original cmdlet is not available a different name is
      // used for the proxy function.
      iss.Commands.Add(new SessionStateFunctionEntry("get-procProxy", bodyOfProxyFunction));

      // Create the constrained runspace using the initial session state.
      using (Runspace myRunspace = RunspaceFactory.CreateRunspace(iss))
      {
        myRunspace.Open();

        // Call the private cmdlet to demonstrate that it is not available.
        try
        {
          using (PowerShell powershell = PowerShell.Create())
          {
            powershell.Runspace = myRunspace;
            powershell.AddCommand("get-proc").AddParameter("Name", "*explore*");
            powershell.Invoke();
          }
        }
        catch (CommandNotFoundException e)
        {
          System.Console.WriteLine(
                        "Invoking 'get-proc' failed as expected: {0}: {1}",
                        e.GetType().FullName,
                        e.Message);
        }

        // Call the proxy function to demonstrate that the -Name parameter is
        // not available.
        try
        {
          using (PowerShell powershell = PowerShell.Create())
          {
            powershell.Runspace = myRunspace;
            powershell.AddCommand("get-procProxy").AddParameter("Name", "idle");
            powershell.Invoke();
          }
        }
        catch (ParameterBindingException e)
        {
          System.Console.WriteLine(
                        "\nInvoking 'get-procProxy -Name idle' failed as expected: {0}: {1}",
                        e.GetType().FullName,
                        e.Message);
        }

        // Call the proxy function to demonstrate that it calls into the
        // private cmdlet to retrieve the processes.
        using (PowerShell powershell = PowerShell.Create())
        {
          powershell.Runspace = myRunspace;
          powershell.AddCommand("get-procProxy");
          List<Process> processes = new List<Process>(powershell.Invoke<Process>());
          System.Console.WriteLine(
                        "\nInvoking the get-procProxy function called into the get-proc cmdlet and returned {0} processes",
                        processes.Count);
        }

        // Close the runspace to release resources.
        myRunspace.Close();
      }

      System.Console.WriteLine("Hit any key to exit...");
      System.Console.ReadKey();
    }
  }
}
```

## <a name="see-also"></a><span data-ttu-id="50dca-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="50dca-120">See Also</span></span>

[<span data-ttu-id="50dca-121">Schreiben Sie eine Windows PowerShell-Hostanwendung</span><span class="sxs-lookup"><span data-stu-id="50dca-121">Writing a Windows PowerShell Host Application</span></span>](./writing-a-windows-powershell-host-application.md)