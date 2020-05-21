---
title: Erstellen eines Workflows mit Windows PowerShell-Aktivitäten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb55971a-4ea4-4c51-aeff-4e0bb05a51b2
caps.latest.revision: 6
ms.openlocfilehash: 12b0b246b78142f3811f9f566cd94e4dabd40cc9
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557464"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a><span data-ttu-id="57808-102">Erstellen eines Workflows mit Windows PowerShell-Aktivitäten</span><span class="sxs-lookup"><span data-stu-id="57808-102">Creating a Workflow with Windows PowerShell Activities</span></span>

<span data-ttu-id="57808-103">Sie können einen Windows PowerShell-Workflow erstellen, indem Sie Aktivitäten aus der Visual Studio-Toolbox auswählen und Sie in das Workflow-Designer Fenster ziehen.</span><span class="sxs-lookup"><span data-stu-id="57808-103">You can create a Windows PowerShell workflow by selecting activities from the Visual Studio Toolbox and dragging them to the Workflow Designer window.</span></span> <span data-ttu-id="57808-104">Weitere Informationen zum Hinzufügen von Windows PowerShell-Aktivitäten zur Visual Studio-Toolbox finden Sie unter [Hinzufügen von Windows PowerShell-Aktivitäten zur Visual Studio-Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span><span class="sxs-lookup"><span data-stu-id="57808-104">For information about adding Windows PowerShell activities to the Visual Studio Toolbox, see [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span></span>

<span data-ttu-id="57808-105">In den folgenden Prozeduren wird beschrieben, wie ein Workflow erstellt wird, der den Domänen Status einer Gruppe von benutzerdefinierten Computern überprüft, Sie einer Domäne zuschließt, wenn Sie noch nicht verknüpft sind, und den Status dann erneut überprüft.</span><span class="sxs-lookup"><span data-stu-id="57808-105">The following procedures describe how to create a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="57808-106">Einrichten des Projekts</span><span class="sxs-lookup"><span data-stu-id="57808-106">Setting up the Project</span></span>

1. <span data-ttu-id="57808-107">Befolgen Sie das Verfahren unter [Hinzufügen von Windows PowerShell-Aktivitäten zur Visual Studio-Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) , um ein Workflow Projekt zu erstellen und die Aktivitäten aus den Assemblys [Microsoft. PowerShell. Activities](/dotnet/api/Microsoft.PowerShell.Activities) und [Microsoft. PowerShell. Management. Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) der Toolbox hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="57808-107">Follow the procedure in [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) to create a workflow project and add the activities from the [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) and [Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) assemblies to the toolbox.</span></span>

2. <span data-ttu-id="57808-108">Fügen Sie "System. Management. Automation", "Microsoft. PowerShell. Activities", "System. Management", "Microsoft. PowerShell. Management. Activities" und "Microsoft. PowerShell. Commands. Management" als Verweisassemblys zum Projekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="57808-108">Add System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities, and Microsoft.PowerShell.Commands.Management as to the project as reference assemblies.</span></span>

### <a name="adding-activities-to-the-workflow"></a><span data-ttu-id="57808-109">Hinzufügen von Aktivitäten zum Workflow</span><span class="sxs-lookup"><span data-stu-id="57808-109">Adding Activities to the Workflow</span></span>

1. <span data-ttu-id="57808-110">Fügen Sie dem Workflow eine **Sequence** -Aktivität hinzu.</span><span class="sxs-lookup"><span data-stu-id="57808-110">Add a **Sequence** activity to the workflow.</span></span>

2. <span data-ttu-id="57808-111">Erstellen Sie ein Argument `ComputerName` mit dem Namen und dem Argumenttyp `String[]` .</span><span class="sxs-lookup"><span data-stu-id="57808-111">Create an argument named `ComputerName` with an argument type of `String[]`.</span></span> <span data-ttu-id="57808-112">Dieses Argument stellt die Namen der Computer dar, die überprüft und verknüpft werden sollen.</span><span class="sxs-lookup"><span data-stu-id="57808-112">This argument represents the names of the computers to check and join.</span></span>

3. <span data-ttu-id="57808-113">Erstellen Sie ein Argument `DomainCred` vom Typ " [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential)".</span><span class="sxs-lookup"><span data-stu-id="57808-113">Create an argument named `DomainCred` of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="57808-114">Dieses Argument stellt die Domänen Anmelde Informationen eines Domänen Kontos dar, das zum Hinzufügen eines Computers zur Domäne autorisiert ist.</span><span class="sxs-lookup"><span data-stu-id="57808-114">This argument represents the domain credentials of a domain account that is authorized to join a computer to the domain.</span></span>

4. <span data-ttu-id="57808-115">Erstellen Sie ein Argument `MachineCred` vom Typ " [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential)".</span><span class="sxs-lookup"><span data-stu-id="57808-115">Create an argument named `MachineCred` of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="57808-116">Dieses Argument stellt die Anmelde Informationen eines Administrators auf den Computern dar, die überprüft und verknüpft werden sollen.</span><span class="sxs-lookup"><span data-stu-id="57808-116">This argument represents the credentials of an administrator on the computers to check and join.</span></span>

5. <span data-ttu-id="57808-117">Fügen Sie eine **ParallelForEach** -Aktivität in der **Sequence** -Aktivität hinzu.</span><span class="sxs-lookup"><span data-stu-id="57808-117">Add a **ParallelForEach** activity inside the **Sequence** activity.</span></span> <span data-ttu-id="57808-118">Geben Sie `comp` und `ComputerName` in die Textfelder ein, sodass die Schleife die Elemente des Arrays durchläuft `ComputerName` .</span><span class="sxs-lookup"><span data-stu-id="57808-118">Enter `comp` and `ComputerName` in the text boxes so that the loop iterates through the elements of the `ComputerName` array.</span></span>

6. <span data-ttu-id="57808-119">Fügen Sie dem Text der **ParallelForEach** -Aktivität eine **Sequence** -Aktivität hinzu.</span><span class="sxs-lookup"><span data-stu-id="57808-119">Add a **Sequence** activity to the body of the **ParallelForEach** activity.</span></span> <span data-ttu-id="57808-120">Legen Sie die **Display Name** -Eigenschaft der Sequenz auf fest `JoinDomain` .</span><span class="sxs-lookup"><span data-stu-id="57808-120">Set the **DisplayName** property of the sequence to `JoinDomain`.</span></span>

7. <span data-ttu-id="57808-121">Fügen Sie der **JoinDomain** -Sequenz eine **getwmiobject** -Aktivität hinzu.</span><span class="sxs-lookup"><span data-stu-id="57808-121">Add a **GetWmiObject** activity to the **JoinDomain** sequence.</span></span>

8. <span data-ttu-id="57808-122">Bearbeiten Sie die Eigenschaften der **getwmiobject** -Aktivität wie folgt.</span><span class="sxs-lookup"><span data-stu-id="57808-122">Edit the properties of the **GetWmiObject** activity as follows.</span></span>

   |<span data-ttu-id="57808-123">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="57808-123">Property</span></span>|<span data-ttu-id="57808-124">Value</span><span class="sxs-lookup"><span data-stu-id="57808-124">Value</span></span>|
   |--------------|-----------|
   |<span data-ttu-id="57808-125">**Class**</span><span class="sxs-lookup"><span data-stu-id="57808-125">**Class**</span></span>|<span data-ttu-id="57808-126">"Win32_ComputerSystem"</span><span class="sxs-lookup"><span data-stu-id="57808-126">"Win32_ComputerSystem"</span></span>|
   |<span data-ttu-id="57808-127">**PSComputerName**</span><span class="sxs-lookup"><span data-stu-id="57808-127">**PSComputerName**</span></span>|<span data-ttu-id="57808-128">zuschreiben</span><span class="sxs-lookup"><span data-stu-id="57808-128">{comp}</span></span>|
   |<span data-ttu-id="57808-129">**PSCredential**</span><span class="sxs-lookup"><span data-stu-id="57808-129">**PSCredential**</span></span>|<span data-ttu-id="57808-130">Machinecred</span><span class="sxs-lookup"><span data-stu-id="57808-130">MachineCred</span></span>|

9. <span data-ttu-id="57808-131">Fügen Sie der **JoinDomain** -Sequenz nach der **getwmiobject** -Aktivität eine **addcomputer** -Aktivität hinzu.</span><span class="sxs-lookup"><span data-stu-id="57808-131">Add an **AddComputer** activity to the **JoinDomain** sequence after the **GetWmiObject** activity.</span></span>

10. <span data-ttu-id="57808-132">Bearbeiten Sie die Eigenschaften der **addcomputer** -Aktivität wie folgt.</span><span class="sxs-lookup"><span data-stu-id="57808-132">Edit the properties of the **AddComputer** activity as follows.</span></span>

    |<span data-ttu-id="57808-133">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="57808-133">Property</span></span>|<span data-ttu-id="57808-134">Value</span><span class="sxs-lookup"><span data-stu-id="57808-134">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="57808-135">**Computername**</span><span class="sxs-lookup"><span data-stu-id="57808-135">**ComputerName**</span></span>|<span data-ttu-id="57808-136">zuschreiben</span><span class="sxs-lookup"><span data-stu-id="57808-136">{comp}</span></span>|
    |<span data-ttu-id="57808-137">**DomainCredential**</span><span class="sxs-lookup"><span data-stu-id="57808-137">**DomainCredential**</span></span>|<span data-ttu-id="57808-138">Domaincred</span><span class="sxs-lookup"><span data-stu-id="57808-138">DomainCred</span></span>|

11. <span data-ttu-id="57808-139">Fügen Sie der **JoinDomain** -Sequenz nach der **addcomputer** -Aktivität eine **restartcomputer** -Aktivität hinzu.</span><span class="sxs-lookup"><span data-stu-id="57808-139">Add a **RestartComputer** activity to the **JoinDomain** sequence after the **AddComputer** activity.</span></span>

12. <span data-ttu-id="57808-140">Bearbeiten Sie die Eigenschaften der **restartcomputer** -Aktivität wie folgt.</span><span class="sxs-lookup"><span data-stu-id="57808-140">Edit the properties of the **RestartComputer** activity as follows.</span></span>

    |<span data-ttu-id="57808-141">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="57808-141">Property</span></span>|<span data-ttu-id="57808-142">Value</span><span class="sxs-lookup"><span data-stu-id="57808-142">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="57808-143">**Computername**</span><span class="sxs-lookup"><span data-stu-id="57808-143">**ComputerName**</span></span>|<span data-ttu-id="57808-144">zuschreiben</span><span class="sxs-lookup"><span data-stu-id="57808-144">{comp}</span></span>|
    |<span data-ttu-id="57808-145">**Credential**</span><span class="sxs-lookup"><span data-stu-id="57808-145">**Credential**</span></span>|<span data-ttu-id="57808-146">Machinecred</span><span class="sxs-lookup"><span data-stu-id="57808-146">MachineCred</span></span>|
    |<span data-ttu-id="57808-147">**Damit**</span><span class="sxs-lookup"><span data-stu-id="57808-147">**For**</span></span>|<span data-ttu-id="57808-148">Microsoft. PowerShell. Commands. waitforservicetypes. PowerShell</span><span class="sxs-lookup"><span data-stu-id="57808-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span></span>|
    |<span data-ttu-id="57808-149">**Force**</span><span class="sxs-lookup"><span data-stu-id="57808-149">**Force**</span></span>|<span data-ttu-id="57808-150">True</span><span class="sxs-lookup"><span data-stu-id="57808-150">True</span></span>|
    |<span data-ttu-id="57808-151">Warten</span><span class="sxs-lookup"><span data-stu-id="57808-151">Wait</span></span>|<span data-ttu-id="57808-152">True</span><span class="sxs-lookup"><span data-stu-id="57808-152">True</span></span>|
    |<span data-ttu-id="57808-153">PSComputerName</span><span class="sxs-lookup"><span data-stu-id="57808-153">PSComputerName</span></span>|<span data-ttu-id="57808-154">{""}</span><span class="sxs-lookup"><span data-stu-id="57808-154">{""}</span></span>|

13. <span data-ttu-id="57808-155">Fügen Sie eine **getwmiobject** -Aktivität der **JoinDomain** -Sequenz nach der **restartcomputer** -Aktivität hinzu.</span><span class="sxs-lookup"><span data-stu-id="57808-155">Add a **GetWmiObject** activity to the **JoinDomain** sequence after the **RestartComputer** activity.</span></span> <span data-ttu-id="57808-156">Bearbeiten Sie die zugehörigen Eigenschaften so, dass Sie mit der vorherigen **getwmiobject** -Aktivität identisch sind.</span><span class="sxs-lookup"><span data-stu-id="57808-156">Edit its properties to be the same as the previous **GetWmiObject** activity.</span></span>

    <span data-ttu-id="57808-157">Wenn Sie die Prozeduren abgeschlossen haben, sollte das Workflow Entwurfs Fenster wie folgt aussehen.</span><span class="sxs-lookup"><span data-stu-id="57808-157">When you have finished the procedures, the workflow design window should look like this.</span></span>

    <span data-ttu-id="57808-158">![JoinDomain XAML im Workflow-Designer ](media/creating-a-workflow-with-windows-powershell-activities/joindomainworkflow.png)
     ![JoinDomain XAML im Workflow-Designer](media/creating-a-workflow-with-windows-powershell-activities/joindomainworkflow.png "Joindomainworkflow")</span><span class="sxs-lookup"><span data-stu-id="57808-158">![JoinDomain XAML in Workflow designer](media/creating-a-workflow-with-windows-powershell-activities/joindomainworkflow.png)
![JoinDomain XAML in Workflow designer](media/creating-a-workflow-with-windows-powershell-activities/joindomainworkflow.png "JoinDomainWorkflow")</span></span>
