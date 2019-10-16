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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366039"
---
# <a name="importing-and-invoking-a-windows-powershell-workflow"></a>Importieren und Aufrufen eines Windows PowerShell-Workflows

Mit Windows PowerShell 3 können Sie einen Workflow importieren und aufrufen, der als Windows PowerShell-Modul verpackt ist. Informationen zu Windows PowerShell-Modulen finden Sie unter [Schreiben eines Windows PowerShell-Moduls](../module/writing-a-windows-powershell-module.md).

Die [System. Management. Automation. psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)-Klasse wird als Client seitiger Proxy für Workflow Objekte auf dem Server verwendet. Im folgenden Verfahren wird erläutert, wie ein [System. Management. Automation. psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy)-Objekt verwendet wird, um einen Workflow aufzurufen.

### <a name="creating-a-psjobproxy-object-to-execute-workflow-commands-on-a-remote-server"></a>Erstellen eines psjobproxy-Objekts zum Ausführen von Workflow Befehlen auf einem Remote Server.

1. Erstellen Sie ein [System. Management. Automation. Runspaces. wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)-Objekt, um eine Verbindung mit einem Remoterunspace herzustellen.

2. Legen Sie die [System. Management. Automation. Runspaces. wsmanconnectioninfo. shelluri *](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo.ShellUri) -Eigenschaft des [System. Management. Automation. Runspaces. wsmanconnectioninfo](/dotnet/api/System.Management.Automation.Runspaces.WSManConnectionInfo)-Objekts auf "`Microsoft.PowerShell.Workflow`" fest, um einen Windows PowerShell-Endpunkt anzugeben.

3. Erstellen Sie einen Runspace, der die mit den vorherigen Schritten erstellte Verbindung verwendet.

4. Erstellen Sie ein [System. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell)-Objekt, und legen Sie dessen Eigenschaft [System. Management. Automation. PowerShell. Runspace *](/dotnet/api/System.Management.Automation.PowerShell.Runspace) auf den im vorherigen Schritt erstellten Runspace fest.

5. Importieren Sie das Workflow Modul und seine Befehle in " [System. Management. Automation. PowerShell](/dotnet/api/System.Management.Automation.PowerShell)".

6. Erstellen Sie ein [System. Management. Automation. psjobproxy](/dotnet/api/System.Management.Automation.PSJobProxy) -Objekt, und verwenden Sie es zum Ausführen von Workflow Befehlen auf dem Remote Server.

## <a name="example"></a>Beispiel

Im folgenden Codebeispiel wird veranschaulicht, wie ein Workflow mithilfe von Windows PowerShell aufgerufen wird.

Für dieses Beispiel ist Windows PowerShell 3 erforderlich.

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