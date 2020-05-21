---
title: Importieren und Aufrufen eines Windows PowerShell-Workflows | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 50e6f9b1-2678-4f53-9250-7c48843a9549
caps.latest.revision: 5
ms.openlocfilehash: a9497d72a586d0cc64c1d4e090819230285767e8
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564965"
---
# <a name="importing-and-invoking-a-windows-powershell-workflow"></a><span data-ttu-id="ded56-102">Importieren und Aufrufen eines Windows PowerShell-Workflows</span><span class="sxs-lookup"><span data-stu-id="ded56-102">Importing and Invoking a Windows PowerShell Workflow</span></span>

<span data-ttu-id="ded56-103">Mit Windows PowerShell 3 können Sie einen Workflow importieren und aufrufen, der als Windows PowerShell-Modul verpackt ist.</span><span class="sxs-lookup"><span data-stu-id="ded56-103">Windows PowerShell 3, allows you to import and invoke a workflow that is packaged as a Windows PowerShell module.</span></span> <span data-ttu-id="ded56-104">Informationen zu Windows PowerShell-Modulen finden Sie unter [Schreiben eines Windows PowerShell-Moduls](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="ded56-104">For information about Windows PowerShell modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

<span data-ttu-id="ded56-105">Die [System. Management. Automation. psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)-Klasse wird als Client seitiger Proxy für Workflow Objekte auf dem Server verwendet.</span><span class="sxs-lookup"><span data-stu-id="ded56-105">The [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)class is used as a client side proxy for workflow objects on the server.</span></span> <span data-ttu-id="ded56-106">Im folgenden Verfahren wird erläutert, wie ein [System. Management. Automation. psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)-Objekt verwendet wird, um einen Workflow aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="ded56-106">The following procedure explains how to use a [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)object to invoke a workflow.</span></span>

### <a name="creating-a-psjobproxy-object-to-execute-workflow-commands-on-a-remote-server"></a><span data-ttu-id="ded56-107">Erstellen eines psjobproxy-Objekts zum Ausführen von Workflow Befehlen auf einem Remote Server.</span><span class="sxs-lookup"><span data-stu-id="ded56-107">Creating a PSJobProxy object to execute workflow commands on a remote server.</span></span>

1. <span data-ttu-id="ded56-108">Erstellen Sie ein [System. Management. Automation. Runspaces. wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)-Objekt, um eine Verbindung mit einem Remoterunspace herzustellen.</span><span class="sxs-lookup"><span data-stu-id="ded56-108">Create an [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)object to create a connection to a remote runspace.</span></span>

2. <span data-ttu-id="ded56-109">Legen Sie die [System. Management. Automation. Runspaces. wsmanconnectioninfo. shelluri \*](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ShellUri) -Eigenschaft des [System. Management. Automation. Runspaces. wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)-Objekts auf fest `Microsoft.PowerShell.Workflow` , um einen Windows PowerShell-Endpunkt anzugeben.</span><span class="sxs-lookup"><span data-stu-id="ded56-109">Set the [System.Management.Automation.Runspaces.Wsmanconnectioninfo.Shelluri\*](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ShellUri) property of the [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)object to `Microsoft.PowerShell.Workflow` to specify a Windows PowerShell endpoint.</span></span>

3. <span data-ttu-id="ded56-110">Erstellen Sie einen Runspace, der die mit den vorherigen Schritten erstellte Verbindung verwendet.</span><span class="sxs-lookup"><span data-stu-id="ded56-110">Create a runspace that uses the connection created by completing the previous steps.</span></span>

4. <span data-ttu-id="ded56-111">Erstellen Sie ein [System. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell)-Objekt, und legen Sie dessen Eigenschaft [System. Management. Automation. PowerShell. Runspace \*](/dotnet/api/System.Management.Automation.PowerShell.Runspace) auf den im vorherigen Schritt erstellten Runspace fest.</span><span class="sxs-lookup"><span data-stu-id="ded56-111">Create a [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell)object and set its [System.Management.Automation.Powershell.Runspace\*](/dotnet/api/System.Management.Automation.PowerShell.Runspace) property to the runspace created in the previous step.</span></span>

5. <span data-ttu-id="ded56-112">Importieren Sie das Workflow Modul und seine Befehle in " [System. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell)".</span><span class="sxs-lookup"><span data-stu-id="ded56-112">Import the workflow module and its commands into the [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell).</span></span>

6. <span data-ttu-id="ded56-113">Erstellen Sie ein [System. Management. Automation. psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy) -Objekt, und verwenden Sie es zum Ausführen von Workflow Befehlen auf dem Remote Server.</span><span class="sxs-lookup"><span data-stu-id="ded56-113">Create a [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy) object and use it to execute workflow commands on the remote server.</span></span>

## <a name="example"></a><span data-ttu-id="ded56-114">Beispiel</span><span class="sxs-lookup"><span data-stu-id="ded56-114">Example</span></span>

<span data-ttu-id="ded56-115">Im folgenden Codebeispiel wird veranschaulicht, wie ein Workflow mithilfe von Windows PowerShell aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="ded56-115">The following code example demonstrates how to invoke a workflow by using Windows PowerShell.</span></span>

<span data-ttu-id="ded56-116">Für dieses Beispiel ist Windows PowerShell 3 erforderlich.</span><span class="sxs-lookup"><span data-stu-id="ded56-116">This example requires Windows PowerShell 3.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Management.Automation;
using System.Management.Automation.Runspaces;

namespace WorkflowHostTest
{

class Program
    {
        static void Main(string[] args)
        {
            if (args.Length == 0)
            {
                Console.WriteLine("Specify path to Workflow module");
                return;
            }

            string moduleFile = args[0];

            Console.Write("Creating Remote runspace connection...");
            WSManConnectionInfo connectionInfo = new WSManConnectionInfo();

            //Set the shellURI to workflow endpoint Microsoft.PowerShell.Workflow
            connectionInfo.ShellUri = "Microsoft.PowerShell.Workflow";

            //Create and open a runspace.
            Runspace runspace = RunspaceFactory.CreateRunspace(connectionInfo);
            runspace.Open();
            Console.WriteLine("done");

            PowerShell powershell = PowerShell.Create();
            powershell.Runspace = runspace;
            Console.Write("Setting $VerbosePreference=\"Continue\"...");
            powershell.AddScript("$VerbosePreference=\"Continue\"");
            powershell.Invoke();
            Console.WriteLine("done");

            Console.Write("Importing Workflow module...");
            powershell.Commands.Clear();

            //Import the module in to the PowerShell runspace. A XAML file could also be imported directly by using Import-Module.
            powershell.AddCommand("Import-Module").AddArgument(moduleFile);
            powershell.Invoke();
            Console.WriteLine("done");

            Console.Write("Creating job proxy...");
            powershell.Commands.Clear();
            powershell.AddCommand("Get-Proc").AddArgument("*");
            PSJobProxy job = powershell.AsJobProxy();
            Console.WriteLine("done");

                Console.WriteLine();
                Console.WriteLine("Using job proxy and performing operations...");
                Console.WriteLine("State of Job :" + job.JobStateInfo.State.ToString());
                Console.WriteLine("Starting job...");
                job.StartJob();
                Console.WriteLine("State of Job :" + job.JobStateInfo.State.ToString());

                // use blocking enumerator to wait for objects until job finishes
                job.Output.BlockingEnumerator = true;
                foreach (PSObject o in job.Output)
                {
                    Console.WriteLine(o.Properties["ProcessName"].Value.ToString());
                }

                // wait for a random time before attempting to stop job
                Random random = new Random();
                int time = random.Next(1, 10);
                Console.Write("Sleeping for {0} seconds when job is running on another thread...", time);
                System.Threading.Thread.Sleep(time * 1000);
                Console.WriteLine("done");
                Console.WriteLine("Stopping job...");
                job.StopJob();
                Console.WriteLine("State of Job :" + job.JobStateInfo.State.ToString());
                Console.WriteLine();
                job.Finished.WaitOne();
                Console.WriteLine("Output from job");
                Console.WriteLine("---------------");

                foreach (PSObject o in job.Output)
                {
                    Console.WriteLine(o.Properties["ProcessName"].Value.ToString());
                }

                Console.WriteLine();
                Console.WriteLine("Verbose messages from job");
                Console.WriteLine("-------------------------");
                foreach (VerboseRecord v in job.Verbose)
                {
                    Console.WriteLine(v.Message);
                }

            runspace.Close();
        }
    }
}

```
