---
title: Hinzufügen von Windows PowerShell-Aktivitäten zu Visual Studio-Toolbox | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: 2a8372d937fc3c959f7d829bb52495048423d506
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56863566"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a><span data-ttu-id="fefbc-102">Hinzufügen von Windows PowerShell-Aktivitäten zur Visual Studio-Toolbox</span><span class="sxs-lookup"><span data-stu-id="fefbc-102">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>

<span data-ttu-id="fefbc-103">Bevor Sie ein PowerShell-Workflow mit Workflow-Designer erstellen, müssen Sie zuerst die PowerShell-Aktivitäten zur Toolbox in ein Visual Studio Workflow-Konsolenanwendungsprojekt hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="fefbc-103">Before you author a PowerShell Workflow using Workflow Designer, you must first add the PowerShell Activities to the Toolbox in a Visual Studio Workflow console application project.</span></span> <span data-ttu-id="fefbc-104">Das folgende Verfahren veranschaulicht das Hinzufügen die Aktivitäten aus der Assembly Microsoft.PowerShell.Core.Activities zur Visual Studio-Toolbox.</span><span class="sxs-lookup"><span data-stu-id="fefbc-104">The following procedure shows how to add the activities from the Microsoft.PowerShell.Core.Activities assembly to the Visual Studio toolbox.</span></span>

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a><span data-ttu-id="fefbc-105">Hinzufügen von Windows PowerShell-Aktivitäten zur Toolbox</span><span class="sxs-lookup"><span data-stu-id="fefbc-105">Adding Windows PowerShell Activities to the Toolbox</span></span>

1. <span data-ttu-id="fefbc-106">Erstellen Sie ein neues Workflow-Konsolenanwendungsprojekt in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fefbc-106">Create a new Workflow console application project in Visual Studio.</span></span>

2. <span data-ttu-id="fefbc-107">Auf der **Ansicht** Menü klicken Sie auf **Toolbox**.</span><span class="sxs-lookup"><span data-stu-id="fefbc-107">On the **View** menu, click **Toolbox**.</span></span>

3. <span data-ttu-id="fefbc-108">Fügen Sie eine neue Registerkarte in der Toolbox hinzu, indem Sie mit der rechten Maustaste in die Toolbox, und auf **Registerkarte hinzufügen**, und benennen Sie der neuen Registerkarte wie"PowerShell".</span><span class="sxs-lookup"><span data-stu-id="fefbc-108">Add a new tab in the Toolbox by right-clicking inside the Toolbox and clicking **Add Tab**, and give the new tab a name such as "PowerShell Activities".</span></span>

   <span data-ttu-id="fefbc-109">Hinzufügen einer Registerkarte können Sie die PowerShell-Aktivitäten, die getrennt von anderen Tools in der Toolbox zu gruppieren.</span><span class="sxs-lookup"><span data-stu-id="fefbc-109">Adding a tab allows you to group the PowerShell Activities separate from other tools in the Toolbox.</span></span>

4. <span data-ttu-id="fefbc-110">Klicken Sie auf die neue Werkzeugkasten-Registerkarte, auf **Elemente auswählen...** . Die **Toolboxelemente** Dialogfeld wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="fefbc-110">On the new Toolbox tab, click **Choose Items...**. The **Choose Toolbox Items** dialog appears.</span></span>

5. <span data-ttu-id="fefbc-111">In der **Toolboxelemente** Dialogfeld klicken Sie auf die **System.Activities** Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="fefbc-111">In the **Choose Toolbox Items** dialog, click the **System.Activities** tab.</span></span>

6. <span data-ttu-id="fefbc-112">Klicken Sie auf **Durchsuchen**.</span><span class="sxs-lookup"><span data-stu-id="fefbc-112">Click **Browse**.</span></span>

7. <span data-ttu-id="fefbc-113">Navigieren Sie zum Ordner %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e, und doppelklicken Sie auf Microsoft.PowerShell.Core.Activities.dll.</span><span class="sxs-lookup"><span data-stu-id="fefbc-113">Navigate to the %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e folder and double-click Microsoft.PowerShell.Core.Activities.dll.</span></span>

8. <span data-ttu-id="fefbc-114">Klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="fefbc-114">Click **OK**.</span></span> <span data-ttu-id="fefbc-115">Die von der Microsoft.PowerShell.Core.Activities-Assembly definierten Aktivitäten sind jetzt in der Toolbox verfügbar.</span><span class="sxs-lookup"><span data-stu-id="fefbc-115">The activities defined by the Microsoft.PowerShell.Core.Activities assembly are now available in the toolbox.</span></span>

## <a name="see-also"></a><span data-ttu-id="fefbc-116">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="fefbc-116">See Also</span></span>

[<span data-ttu-id="fefbc-117">Schreiben eines PowerShell-Workflows</span><span class="sxs-lookup"><span data-stu-id="fefbc-117">Writing a Windows PowerShell Workflow</span></span>](./writing-a-windows-powershell-workflow.md)

[<span data-ttu-id="fefbc-118">Erstellen eines Workflows mit Windows PowerShell-Aktivitäten</span><span class="sxs-lookup"><span data-stu-id="fefbc-118">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)