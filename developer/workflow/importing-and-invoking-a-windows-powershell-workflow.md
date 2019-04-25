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
ms.openlocfilehash: 1113c0d1cd68bb97d2f96b529f755b62137d1f40
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080338"
---
# <a name="importing-and-invoking-a-windows-powershell-workflow"></a><span data-ttu-id="466a3-102">Importieren und Aufrufen eines Windows PowerShell-Workflows</span><span class="sxs-lookup"><span data-stu-id="466a3-102">Importing and Invoking a Windows PowerShell Workflow</span></span>

<span data-ttu-id="466a3-103">Windows PowerShell 3, können Sie zum Importieren und Aufrufen eines Workflows, das als ein Windows PowerShell-Modul verpackt wird.</span><span class="sxs-lookup"><span data-stu-id="466a3-103">Windows PowerShell 3, allows you to import and invoke a workflow that is packaged as a Windows PowerShell module.</span></span> <span data-ttu-id="466a3-104">Informationen zu Windows PowerShell-Modulen, finden Sie unter [Schreiben eines Windows PowerShell-Moduls](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="466a3-104">For information about Windows PowerShell modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

<span data-ttu-id="466a3-105">Die [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)Klasse wird als einen clientseitigen Proxy für Workflow-Objekte, auf dem Server verwendet.</span><span class="sxs-lookup"><span data-stu-id="466a3-105">The [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)class is used as a client side proxy for workflow objects on the server.</span></span> <span data-ttu-id="466a3-106">Das folgende Verfahren erläutert, wie eine [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)Objekt, das Aufrufen eines Workflows.</span><span class="sxs-lookup"><span data-stu-id="466a3-106">The following procedure explains how to use a [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)object to invoke a workflow.</span></span>

### <a name="creating-a-psjobproxy-object-to-execute-workflow-commands-on-a-remote-server"></a><span data-ttu-id="466a3-107">Erstellen ein PSJobProxy-Objekt, um die Workflowbefehle auf einem Remoteserver auszuführen.</span><span class="sxs-lookup"><span data-stu-id="466a3-107">Creating a PSJobProxy object to execute workflow commands on a remote server.</span></span>

1. <span data-ttu-id="466a3-108">Erstellen Sie eine [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)Objekt, das eine Verbindung mit einen Remoterunspace erstellen.</span><span class="sxs-lookup"><span data-stu-id="466a3-108">Create an [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)object to create a connection to a remote runspace.</span></span>

2. <span data-ttu-id="466a3-109">Legen Sie die [System.Management.Automation.Runspaces.Wsmanconnectioninfo.Shelluri\*](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ShellUri) Eigenschaft der [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)-Objekt `Microsoft.PowerShell.Workflow` auf Geben Sie einen Windows PowerShell-Endpunkt.</span><span class="sxs-lookup"><span data-stu-id="466a3-109">Set the [System.Management.Automation.Runspaces.Wsmanconnectioninfo.Shelluri\*](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ShellUri) property of the [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)object to `Microsoft.PowerShell.Workflow` to specify a Windows PowerShell endpoint.</span></span>

3. <span data-ttu-id="466a3-110">Erstellen Sie einen Runspace, der die Verbindung mithilfe der vorherigen Schritte erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="466a3-110">Create a runspace that uses the connection created by completing the previous steps.</span></span>

4. <span data-ttu-id="466a3-111">Erstellen Sie eine [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell)Objekt, und legen seine [System.Management.Automation.Powershell.Runspace\*](/dotnet/api/System.Management.Automation.PowerShell.Runspace) Eigenschaft mit dem Runspace, die im vorherigen Schritt erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="466a3-111">Create a [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell)object and set its [System.Management.Automation.Powershell.Runspace\*](/dotnet/api/System.Management.Automation.PowerShell.Runspace) property to the runspace created in the previous step.</span></span>

5. <span data-ttu-id="466a3-112">Importieren Sie das Workflowmodul und die Befehle in der [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell).</span><span class="sxs-lookup"><span data-stu-id="466a3-112">Import the workflow module and its commands into the [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell).</span></span>

6. <span data-ttu-id="466a3-113">Erstellen Sie eine [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy) Objekt aus, und verwenden, um die Workflowbefehle auf dem Remoteserver ausführen.</span><span class="sxs-lookup"><span data-stu-id="466a3-113">Create a [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy) object and use it to execute workflow commands on the remote server.</span></span>

## <a name="example"></a><span data-ttu-id="466a3-114">Beispiel</span><span class="sxs-lookup"><span data-stu-id="466a3-114">Example</span></span>

<span data-ttu-id="466a3-115">Im folgenden Codebeispiel wird veranschaulicht, wie einen Workflow aufgerufen wird, mithilfe von Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="466a3-115">The following code example demonstrates how to invoke a workflow by using Windows PowerShell.</span></span>

<span data-ttu-id="466a3-116">In diesem Beispiel ist die Windows PowerShell 3 erforderlich.</span><span class="sxs-lookup"><span data-stu-id="466a3-116">This example requires Windows PowerShell 3.</span></span>

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