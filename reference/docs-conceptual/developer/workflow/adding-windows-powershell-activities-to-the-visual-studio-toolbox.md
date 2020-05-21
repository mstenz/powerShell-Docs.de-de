---
title: Hinzufügen von Windows PowerShell-Aktivitäten zur Visual Studio-Toolbox | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c8ef289-0659-42d1-9976-044b144201eb
caps.latest.revision: 6
ms.openlocfilehash: ecd23d3eb722137bdda0498fc71e0e966c57a589
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83561188"
---
# <a name="adding-windows-powershell-activities-to-the-visual-studio-toolbox"></a><span data-ttu-id="b7f40-102">Hinzufügen von Windows PowerShell-Aktivitäten zur Visual Studio-Toolbox</span><span class="sxs-lookup"><span data-stu-id="b7f40-102">Adding Windows PowerShell Activities to the Visual Studio Toolbox</span></span>

<span data-ttu-id="b7f40-103">Bevor Sie einen PowerShell-Workflow mithilfe von Workflow-Designer erstellen, müssen Sie die PowerShell-Aktivitäten zunächst der Toolbox in einem Konsolen Anwendungsprojekt von Visual Studio Workflow hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="b7f40-103">Before you author a PowerShell Workflow using Workflow Designer, you must first add the PowerShell Activities to the Toolbox in a Visual Studio Workflow console application project.</span></span> <span data-ttu-id="b7f40-104">Im folgenden Verfahren wird gezeigt, wie die Aktivitäten aus der Microsoft. PowerShell. Core. Activities-Assembly der Visual Studio-Toolbox hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="b7f40-104">The following procedure shows how to add the activities from the Microsoft.PowerShell.Core.Activities assembly to the Visual Studio toolbox.</span></span>

### <a name="adding-windows-powershell-activities-to-the-toolbox"></a><span data-ttu-id="b7f40-105">Hinzufügen von Windows PowerShell-Aktivitäten zur Toolbox</span><span class="sxs-lookup"><span data-stu-id="b7f40-105">Adding Windows PowerShell Activities to the Toolbox</span></span>

1. <span data-ttu-id="b7f40-106">Erstellen Sie in Visual Studio ein neues Projekt für eine Workflow Konsolenanwendung.</span><span class="sxs-lookup"><span data-stu-id="b7f40-106">Create a new Workflow console application project in Visual Studio.</span></span>

2. <span data-ttu-id="b7f40-107">Klicken Sie im Menü **Ansicht** auf **Toolbox**.</span><span class="sxs-lookup"><span data-stu-id="b7f40-107">On the **View** menu, click **Toolbox**.</span></span>

3. <span data-ttu-id="b7f40-108">Fügen Sie eine neue Registerkarte in der Toolbox hinzu, indem Sie mit der rechten Maustaste in die Toolbox klicken und auf **Registerkarte hinzufügen**klicken und der neuen Registerkarte einen Namen wie "PowerShell-Aktivitäten" geben.</span><span class="sxs-lookup"><span data-stu-id="b7f40-108">Add a new tab in the Toolbox by right-clicking inside the Toolbox and clicking **Add Tab**, and give the new tab a name such as "PowerShell Activities".</span></span>

   <span data-ttu-id="b7f40-109">Durch das Hinzufügen einer Registerkarte können Sie die PowerShell-Aktivitäten getrennt von anderen Tools in der Toolbox gruppieren.</span><span class="sxs-lookup"><span data-stu-id="b7f40-109">Adding a tab allows you to group the PowerShell Activities separate from other tools in the Toolbox.</span></span>

4. <span data-ttu-id="b7f40-110">Klicken Sie auf der Registerkarte neue Toolbox auf **Elemente auswählen...**. Das Dialogfeld **Toolbox Elemente auswählen** wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b7f40-110">On the new Toolbox tab, click **Choose Items...**. The **Choose Toolbox Items** dialog appears.</span></span>

5. <span data-ttu-id="b7f40-111">Klicken Sie im Dialogfeld **Toolbox Elemente auswählen** auf die Registerkarte **System. Activities** .</span><span class="sxs-lookup"><span data-stu-id="b7f40-111">In the **Choose Toolbox Items** dialog, click the **System.Activities** tab.</span></span>

6. <span data-ttu-id="b7f40-112">Klicken Sie auf **Durchsuchen**.</span><span class="sxs-lookup"><span data-stu-id="b7f40-112">Click **Browse**.</span></span>

7. <span data-ttu-id="b7f40-113">Navigieren Sie zum Ordner%windir%\Microsoft.net\assembly\ GAC_MSIL \Microsoft.PowerShell.Core.activities\v4.0_3.0.0.0__31bf3856ad364e, und doppelklicken Sie auf Microsoft. PowerShell. Core. Activities. dll.</span><span class="sxs-lookup"><span data-stu-id="b7f40-113">Navigate to the %WINDIR%\Microsoft.NET\assembly\GAC_MSIL\Microsoft.PowerShell.Core.Activities\v4.0_3.0.0.0__31bf3856ad364e folder and double-click Microsoft.PowerShell.Core.Activities.dll.</span></span>

8. <span data-ttu-id="b7f40-114">Klicken Sie auf **OK**.</span><span class="sxs-lookup"><span data-stu-id="b7f40-114">Click **OK**.</span></span> <span data-ttu-id="b7f40-115">Die von der Microsoft. PowerShell. Core. Activities-Assembly definierten Aktivitäten sind jetzt in der Toolbox verfügbar.</span><span class="sxs-lookup"><span data-stu-id="b7f40-115">The activities defined by the Microsoft.PowerShell.Core.Activities assembly are now available in the toolbox.</span></span>

## <a name="see-also"></a><span data-ttu-id="b7f40-116">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b7f40-116">See Also</span></span>

[<span data-ttu-id="b7f40-117">Schreiben Sie einen Windows PowerShell-Workflow</span><span class="sxs-lookup"><span data-stu-id="b7f40-117">Writing a Windows PowerShell Workflow</span></span>](./writing-a-windows-powershell-workflow.md)

[<span data-ttu-id="b7f40-118">Erstellen eines Workflows mit Windows PowerShell-Aktivitäten</span><span class="sxs-lookup"><span data-stu-id="b7f40-118">Creating a Workflow with Windows PowerShell Activities</span></span>](./creating-a-workflow-with-windows-powershell-activities.md)
