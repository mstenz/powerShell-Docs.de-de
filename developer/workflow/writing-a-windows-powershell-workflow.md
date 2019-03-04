---
title: Writing a Windows PowerShell-Workflow | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2551ceed-836f-4275-9fc0-ea68446d6a35
caps.latest.revision: 7
ms.openlocfilehash: 4f0be193fb5b5c753d040a48e5f49235ece11708
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857406"
---
# <a name="writing-a-windows-powershell-workflow"></a><span data-ttu-id="8a4d4-102">Schreiben Sie einen Windows PowerShell-Workflow</span><span class="sxs-lookup"><span data-stu-id="8a4d4-102">Writing a Windows PowerShell Workflow</span></span>

<span data-ttu-id="8a4d4-103">Sie können einen XAML-Workflow erstellen, durch das Hinzufügen von Aktivitäten, die von Windows PowerShell-Assemblys zum Workflow-Designer in Visual Studio verfügbar gemacht werden.</span><span class="sxs-lookup"><span data-stu-id="8a4d4-103">You can create a XAML workflow by adding activities exposed by Windows PowerShell assemblies to the Workflow designer in Visual Studio.</span></span> <span data-ttu-id="8a4d4-104">Die folgenden Windows PowerShell-Assemblys verfügbar machen, Workflow-fähiger Aktivitäten.</span><span class="sxs-lookup"><span data-stu-id="8a4d4-104">The following Windows PowerShell assemblies expose workflow-enabled activities.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8a4d4-105">Wenn Sie Hilfe für den Workflow bereitstellen möchten, muss ein XAML-Workflow als Modul verpackt werden.</span><span class="sxs-lookup"><span data-stu-id="8a4d4-105">A XAML workflow must be packaged as a module if you want to provide help for the workflow.</span></span> <span data-ttu-id="8a4d4-106">Weitere Informationen zu Modulen finden Sie unter [Schreiben eines Windows PowerShell-Moduls](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="8a4d4-106">For information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

- [<span data-ttu-id="8a4d4-107">Microsoft.Powershell.Activities</span><span class="sxs-lookup"><span data-stu-id="8a4d4-107">Microsoft.Powershell.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Activities)

- [<span data-ttu-id="8a4d4-108">Microsoft.Powershell.Core.Activities</span><span class="sxs-lookup"><span data-stu-id="8a4d4-108">Microsoft.Powershell.Core.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Core.Activities)

- [<span data-ttu-id="8a4d4-109">Microsoft.Powershell.Diagnostics.Activities</span><span class="sxs-lookup"><span data-stu-id="8a4d4-109">Microsoft.Powershell.Diagnostics.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Diagnostics.Activities)

- [<span data-ttu-id="8a4d4-110">Microsoft.Powershell.Management.Activities</span><span class="sxs-lookup"><span data-stu-id="8a4d4-110">Microsoft.Powershell.Management.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Management.Activities)

- [<span data-ttu-id="8a4d4-111">Microsoft.Powershell.Security.Activities</span><span class="sxs-lookup"><span data-stu-id="8a4d4-111">Microsoft.Powershell.Security.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Security.Activities)

- [<span data-ttu-id="8a4d4-112">Microsoft.Powershell.Utility.Activities</span><span class="sxs-lookup"><span data-stu-id="8a4d4-112">Microsoft.Powershell.Utility.Activities</span></span>](/dotnet/api/Microsoft.PowerShell.Utility.Activities)

  <span data-ttu-id="8a4d4-113">In den folgenden Themen wird beschrieben, wie zum Erstellen eines Workflows mit Windows PowerShell-Aktivitäten.</span><span class="sxs-lookup"><span data-stu-id="8a4d4-113">The following topics describe how to create a Workflow by using Windows PowerShell activities.</span></span>

- [<span data-ttu-id="8a4d4-114">Hinzufügen von Windows PowerShell-Aktivitäten zur Toolbox von Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8a4d4-114">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md)

- [<span data-ttu-id="8a4d4-115">Erstellen eines Workflows mit Windows PowerShell-Aktivitäten</span><span class="sxs-lookup"><span data-stu-id="8a4d4-115">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)

- [<span data-ttu-id="8a4d4-116">Erstellen eines Workflows mithilfe eines Windows PowerShell-Skripts</span><span class="sxs-lookup"><span data-stu-id="8a4d4-116">Creating a Workflow by Using a Windows PowerShell Script</span></span>](./creating-a-workflow-by-using-a-windows-powershell-script.md)

- [<span data-ttu-id="8a4d4-117">Importieren und Aufrufen eines Windows PowerShell-Workflows</span><span class="sxs-lookup"><span data-stu-id="8a4d4-117">Importing and Invoking a Windows PowerShell Workflow</span></span>](./importing-and-invoking-a-windows-powershell-workflow.md)

- [<span data-ttu-id="8a4d4-118">Creating a Workflow Activity from a Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8a4d4-118">Creating a Workflow Activity from a Windows PowerShell Cmdlet</span></span>](./creating-a-workflow-activity-from-a-windows-powershell-cmdlet.md)