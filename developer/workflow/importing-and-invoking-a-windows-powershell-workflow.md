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
# <a name="importing-and-invoking-a-windows-powershell-workflow"></a>Importieren und Aufrufen eines Windows PowerShell-Workflows

Windows PowerShell 3, können Sie zum Importieren und Aufrufen eines Workflows, das als ein Windows PowerShell-Modul verpackt wird. Informationen zu Windows PowerShell-Modulen, finden Sie unter [Schreiben eines Windows PowerShell-Moduls](../module/writing-a-windows-powershell-module.md).

Die [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)Klasse wird als einen clientseitigen Proxy für Workflow-Objekte, auf dem Server verwendet. Das folgende Verfahren erläutert, wie eine [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)Objekt, das Aufrufen eines Workflows.

### <a name="creating-a-psjobproxy-object-to-execute-workflow-commands-on-a-remote-server"></a>Erstellen ein PSJobProxy-Objekt, um die Workflowbefehle auf einem Remoteserver auszuführen.

1. Erstellen Sie eine [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)Objekt, das eine Verbindung mit einen Remoterunspace erstellen.

2. Legen Sie die [System.Management.Automation.Runspaces.Wsmanconnectioninfo.Shelluri*](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ShellUri) Eigenschaft der [System.Management.Automation.Runspaces.Wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)-Objekt `Microsoft.PowerShell.Workflow` auf Geben Sie einen Windows PowerShell-Endpunkt.

3. Erstellen Sie einen Runspace, der die Verbindung mithilfe der vorherigen Schritte erstellt wird.

4. Erstellen Sie eine [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell)Objekt, und legen seine [System.Management.Automation.Powershell.Runspace*](/dotnet/api/System.Management.Automation.PowerShell.Runspace) Eigenschaft mit dem Runspace, die im vorherigen Schritt erstellt haben.

5. Importieren Sie das Workflowmodul und die Befehle in der [System.Management.Automation.Powershell](/dotnet/api/System.Management.Automation.PowerShell).

6. Erstellen Sie eine [System.Management.Automation.Psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy) Objekt aus, und verwenden, um die Workflowbefehle auf dem Remoteserver ausführen.

## <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird veranschaulicht, wie einen Workflow aufgerufen wird, mithilfe von Windows PowerShell.

In diesem Beispiel ist die Windows PowerShell 3 erforderlich.

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