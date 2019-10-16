---
title: Erstellen einer Workflow Aktivität aus einem Windows PowerShell-Cmdlet | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4174e84f-d516-4aca-b418-273047dcfb07
caps.latest.revision: 7
ms.openlocfilehash: 5761ed2168a46d6ed9a2e50554d459f5b93223ee
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359659"
---
# <a name="creating-a-workflow-activity-from-a-windows-powershell-cmdlet"></a><span data-ttu-id="8c982-102">Erstellen einer Workflowaktivität mit einem Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8c982-102">Creating a Workflow Activity from a Windows PowerShell Cmdlet</span></span>

<span data-ttu-id="8c982-103">Alle Windows PowerShell-Module oder-Cmdlets können mithilfe der Methoden der [Microsoft. PowerShell. Activities. activitygenerator](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator) -Klasse als Workflow Aktivität verpackt werden.</span><span class="sxs-lookup"><span data-stu-id="8c982-103">Any Windows PowerShell module or cmdlet can be packaged as a Workflow activity by using the methods of the [Microsoft.Powershell.Activities.Activitygenerator](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator) class.</span></span> <span data-ttu-id="8c982-104">Verwenden Sie [Microsoft. PowerShell. Activities. activitygenerator. generatefrommoduleinfo \*](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromModuleInfo), [Microsoft. PowerShell. Activities. activitygenerator. generatefromcommandinfo \*](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromCommandInfo)und [ Microsoft. PowerShell. Activities. activitygenerator. generatefromname \*](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromName) -Methoden der [Microsoft. PowerShell. Activities. activitygenerator](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator) -Klasse, C# um Code zu generieren, der eine Aktivität darstellt.</span><span class="sxs-lookup"><span data-stu-id="8c982-104">Use the [Microsoft.Powershell.Activities.Activitygenerator.Generatefrommoduleinfo\*](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromModuleInfo), [Microsoft.Powershell.Activities.Activitygenerator.Generatefromcommandinfo\*](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromCommandInfo), and [Microsoft.Powershell.Activities.Activitygenerator.Generatefromname\*](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator.GenerateFromName) methods of the [Microsoft.Powershell.Activities.Activitygenerator](/dotnet/api/Microsoft.PowerShell.Activities.ActivityGenerator) class to generate C# code that represents an activity.</span></span> <span data-ttu-id="8c982-105">Anschließend können Sie den resultierenden C# Code in eine Assembly kompilieren, die einem Projekt als Aktivität hinzugefügt werden kann.</span><span class="sxs-lookup"><span data-stu-id="8c982-105">You can then compile the resulting C# code into an assembly that can be added to a project as an activity.</span></span>

<span data-ttu-id="8c982-106">Anschließend können Sie den resultierenden C# Code in eine Assembly kompilieren, die einem Projekt als Aktivität hinzugefügt werden kann, indem Sie eine Befehlszeile mit dem folgenden Formular verwenden.</span><span class="sxs-lookup"><span data-stu-id="8c982-106">You can then compile the resulting C# code into an assembly that can be added to a project as an activity by using a command line with the following form.</span></span>

<span data-ttu-id="8c982-107">**CSC/nologo/out: AssemblyName/target: Library/Reference: System. Activities. Activity/Reference: Microsoft. PowerShell. Activities CodeFile.cs**</span><span class="sxs-lookup"><span data-stu-id="8c982-107">**csc /nologo /out:AssemblyName /target:library /reference:System.Activities.Activity /reference:Microsoft.PowerShell.Activities codefile.cs**</span></span>

## <a name="example"></a><span data-ttu-id="8c982-108">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8c982-108">Example</span></span>

<span data-ttu-id="8c982-109">Im folgenden Beispiel wird veranschaulicht, wie C# Code für eine Aktivität aus einem Windows PowerShell-Modul generiert wird.</span><span class="sxs-lookup"><span data-stu-id="8c982-109">The following example demonstrates how to generate C# code for an activity from a Windows PowerShell module.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.IO;
using System.Management.Automation;
using System.Collections.ObjectModel;
using Microsoft.PowerShell.Activities;

namespace MakeActivity
{
    class Program
    {
        static void Main(string[] args)

        {
            StreamWriter CodeFile = new StreamWriter("c:\\\\testmodule\\codefile.cs");
            Collection<PSModuleInfo> ModuleInfos = new Collection<PSModuleInfo> { };
            PSModuleInfo ModuleInfo;
            string ActivityCode = "";
            string ModulePath = "";
            Console.Write("Type the full path and filename of the module to process:");
            ModulePath = Console.ReadLine();

            PowerShell ps = PowerShell.Create();

            ps.AddCommand("Import-Module").AddArgument(ModulePath);
            ps.AddParameter("PassThru");
            ModuleInfos = ps.Invoke<PSModuleInfo>();

            ModuleInfo = (PSModuleInfo)ModuleInfos[0];

            ActivityCode = ActivityGenerator.GenerateFromModuleInfo(ModuleInfo, "MyNamespace").First<String>();

           CodeFile.Write(ActivityCode);
            Console.ReadLine();

        }
    }
}

```

## <a name="example"></a><span data-ttu-id="8c982-110">Beispiel</span><span class="sxs-lookup"><span data-stu-id="8c982-110">Example</span></span>

<span data-ttu-id="8c982-111">Im folgenden Beispiel wird veranschaulicht, wie C# Code für eine Aktivität aus einem Windows PowerShell-Cmdlet generiert wird.</span><span class="sxs-lookup"><span data-stu-id="8c982-111">The following example demonstrates how to generate C# code for an activity from a Windows PowerShell cmdlet.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.IO;
using System.Management.Automation;
using System.Collections.ObjectModel;
using Microsoft.PowerShell.Activities;

namespace MakeActivity
{
    class Program
    {
        static void Main(string[] args)

        {
            StreamWriter CodeFile = new StreamWriter("c:\\\\testmodule\\codefile.cs");
            Collection<PSModuleInfo> ModuleInfos = new Collection<PSModuleInfo> { };
            PSModuleInfo ModuleInfo;
            Collection<CommandInfo> CommandInfos = new Collection<CommandInfo> { };
            CommandInfo MyCommand;
            string ActivityCode = "";
            string ModulePath = "";
            Console.Write("Type the full path and filename of the module to process:");
            ModulePath = Console.ReadLine();

            PowerShell ps = PowerShell.Create();

            ps.AddCommand("Import-Module").AddArgument(ModulePath);
            ps.AddParameter("PassThru");
            ModuleInfos = ps.Invoke<PSModuleInfo>();

            ModuleInfo = (PSModuleInfo)ModuleInfos[0];

            ps.AddCommand("Get-Command").AddArgument(ModuleInfo);
            CommandInfos = ps.Invoke<CommandInfo>();

            MyCommand = CommandInfos[0];

            ActivityCode = ActivityGenerator.GenerateFromCommandInfo(MyCommand, "MyNamespace");

           CodeFile.Write(ActivityCode);
            Console.ReadLine();

        }
    }
}

```