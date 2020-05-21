---
title: Schreiben eines Windows PowerShell-Workflows | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2551ceed-836f-4275-9fc0-ea68446d6a35
caps.latest.revision: 7
ms.openlocfilehash: 0f8a9938a1685e9abc2f1dbfb18c3b2b9008d9be
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564925"
---
# <a name="writing-a-windows-powershell-workflow"></a><span data-ttu-id="d7be8-102">Schreiben Sie einen Windows PowerShell-Workflow</span><span class="sxs-lookup"><span data-stu-id="d7be8-102">Writing a Windows PowerShell Workflow</span></span>

<span data-ttu-id="d7be8-103">Sie können einen XAML-Workflow erstellen, indem Sie dem Workflow-Designer in Visual Studio Aktivitäten hinzufügen, die von Windows PowerShell-Assemblys verfügbar gemacht</span><span class="sxs-lookup"><span data-stu-id="d7be8-103">You can create a XAML workflow by adding activities exposed by Windows PowerShell assemblies to the Workflow designer in Visual Studio.</span></span> <span data-ttu-id="d7be8-104">Die folgenden Windows PowerShell-Assemblys machen Workflow aktivierte Aktivitäten verfügbar.</span><span class="sxs-lookup"><span data-stu-id="d7be8-104">The following Windows PowerShell assemblies expose workflow-enabled activities.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d7be8-105">Ein XAML-Workflow muss als Modul verpackt werden, wenn Sie Hilfe für den Workflow bereitstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="d7be8-105">A XAML workflow must be packaged as a module if you want to provide help for the workflow.</span></span> <span data-ttu-id="d7be8-106">Weitere Informationen zu Modulen finden Sie unter [Schreiben eines Windows PowerShell-Moduls](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="d7be8-106">For information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

- [<span data-ttu-id="d7be8-107">Microsoft. PowerShell. Activities</span><span class="sxs-lookup"><span data-stu-id="d7be8-107">Microsoft.Powershell.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Activities)

- [<span data-ttu-id="d7be8-108">Microsoft. PowerShell. Core. Activities</span><span class="sxs-lookup"><span data-stu-id="d7be8-108">Microsoft.Powershell.Core.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Core.Activities)

- [<span data-ttu-id="d7be8-109">Microsoft. PowerShell. Diagnostics. Activities</span><span class="sxs-lookup"><span data-stu-id="d7be8-109">Microsoft.Powershell.Diagnostics.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Diagnostics.Activities)

- [<span data-ttu-id="d7be8-110">Microsoft. PowerShell. Management. Activities</span><span class="sxs-lookup"><span data-stu-id="d7be8-110">Microsoft.Powershell.Management.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Management.Activities)

- [<span data-ttu-id="d7be8-111">Microsoft. PowerShell. Security. Activities</span><span class="sxs-lookup"><span data-stu-id="d7be8-111">Microsoft.Powershell.Security.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Security.Activities)

- [<span data-ttu-id="d7be8-112">Microsoft. PowerShell. Utility. Activities</span><span class="sxs-lookup"><span data-stu-id="d7be8-112">Microsoft.Powershell.Utility.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Utility.Activities)

  <span data-ttu-id="d7be8-113">In den folgenden Themen wird beschrieben, wie ein Workflow mithilfe von Windows PowerShell-Aktivitäten erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="d7be8-113">The following topics describe how to create a Workflow by using Windows PowerShell activities.</span></span>

- [<span data-ttu-id="d7be8-114">Hinzufügen von Windows PowerShell-Aktivitäten zur Visual Studio-Toolbox</span><span class="sxs-lookup"><span data-stu-id="d7be8-114">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)

- [<span data-ttu-id="d7be8-115">Erstellen eines Workflows mit Windows PowerShell-Aktivitäten</span><span class="sxs-lookup"><span data-stu-id="d7be8-115">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)

- [<span data-ttu-id="d7be8-116">Erstellen eines Workflows mit einem Windows PowerShell-Skript</span><span class="sxs-lookup"><span data-stu-id="d7be8-116">Creating a Workflow by Using a Windows PowerShell Script</span></span>](./creating-a-workflow-by-using-a-windows-powershell-script.md)

- [<span data-ttu-id="d7be8-117">Importieren und Aufrufen eines Windows PowerShell-Workflows</span><span class="sxs-lookup"><span data-stu-id="d7be8-117">Importing and Invoking a Windows PowerShell Workflow</span></span>](./importing-and-invoking-a-windows-powershell-workflow.md)

- [<span data-ttu-id="d7be8-118">Erstellen einer Workflowaktivität mit einem Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="d7be8-118">Creating a Workflow Activity from a Windows PowerShell Cmdlet</span></span>](./creating-a-workflow-activity-from-a-windows-powershell-cmdlet.md)
