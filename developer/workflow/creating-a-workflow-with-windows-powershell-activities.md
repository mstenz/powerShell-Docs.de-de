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
ms.openlocfilehash: 65d04c526ef7aa112da82adb924c0789731f3850
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853466"
---
# <a name="creating-a-workflow-with-windows-powershell-activities"></a><span data-ttu-id="0e8ee-102">Erstellen eines Workflows mit Windows PowerShell-Aktivitäten</span><span class="sxs-lookup"><span data-stu-id="0e8ee-102">Creating a Workflow with Windows PowerShell Activities</span></span>

<span data-ttu-id="0e8ee-103">Sie können einen Windows PowerShell-Workflow erstellen, durch Auswählen von Aktivitäten in der Visual Studio-Toolbox und ziehen sie an das Workflow-Designer-Fenster.</span><span class="sxs-lookup"><span data-stu-id="0e8ee-103">You can create a Windows PowerShell workflow by selecting activities from the Visual Studio Toolbox and dragging them to the Workflow Designer window.</span></span> <span data-ttu-id="0e8ee-104">Informationen zum Hinzufügen von Windows PowerShell-Aktivitäten zu Visual Studio-Toolbox finden Sie unter [Hinzufügen von Windows PowerShell-Aktivitäten, die Visual Studio-Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span><span class="sxs-lookup"><span data-stu-id="0e8ee-104">For information about adding Windows PowerShell activities to the Visual Studio Toolbox, see [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md).</span></span>

<span data-ttu-id="0e8ee-105">Die folgenden Verfahren wird beschrieben, wie zum Erstellen eines Workflows, die sie mit einer Domäne verknüpft werden, wenn sie nicht bereits verknüpft sind, und klicken Sie dann erneut den Status überprüft überprüft den Domänenstatus einer Gruppe von Benutzer angegebenen Computer.</span><span class="sxs-lookup"><span data-stu-id="0e8ee-105">The following procedures describe how to create a workflow that checks the domain status of a group of user-specified computers, joins them to a domain if they are not already joined, and then checks the status again.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="0e8ee-106">Einrichten des Projekts</span><span class="sxs-lookup"><span data-stu-id="0e8ee-106">Setting up the Project</span></span>

1. <span data-ttu-id="0e8ee-107">Führen Sie die Verfahren in [Hinzufügen von Windows PowerShell-Aktivitäten, die Visual Studio-Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) erstellen ein Workflowprojekt und Hinzufügen von Aktivitäten aus der [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) und [ Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) Assemblys zur Toolbox.</span><span class="sxs-lookup"><span data-stu-id="0e8ee-107">Follow the procedure in [Adding Windows PowerShell Activities to the Visual Studio Toolbox](./adding-windows-powershell-activities-to-the-visual-studio-toolbox.md) to create a workflow project and add the activities from the [Microsoft.Powershell.Activities](/dotnet/api/Microsoft.PowerShell.Activities) and [Microsoft.Powershell.Management.Activities](/dotnet/api/Microsoft.PowerShell.Management.Activities) assemblies to the toolbox.</span></span>

2. <span data-ttu-id="0e8ee-108">System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities und Microsoft.PowerShell.Commands.Management als referenzassemblys, dem Projekt hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="0e8ee-108">Add System.Management.Automation, Microsoft.PowerShell.Activities, System.Management, Microsoft.PowerShell.Management.Activities, and Microsoft.PowerShell.Commands.Management as to the project as reference assemblies.</span></span>

### <a name="adding-activities-to-the-workflow"></a><span data-ttu-id="0e8ee-109">Hinzufügen von Aktivitäten zu Workflows</span><span class="sxs-lookup"><span data-stu-id="0e8ee-109">Adding Activities to the Workflow</span></span>

1. <span data-ttu-id="0e8ee-110">Hinzufügen einer **Sequenz** -Aktivität zum Workflow.</span><span class="sxs-lookup"><span data-stu-id="0e8ee-110">Add a **Sequence** activity to the workflow.</span></span>

2. <span data-ttu-id="0e8ee-111">Erstellen Sie ein Argument mit dem Namen `ComputerName` mit Argumenttyp `String[]`.</span><span class="sxs-lookup"><span data-stu-id="0e8ee-111">Create an argument named `ComputerName` with an argument type of `String[]`.</span></span> <span data-ttu-id="0e8ee-112">Dieses Argument stellt den Namen der Computer zu überprüfen und zu verknüpfen.</span><span class="sxs-lookup"><span data-stu-id="0e8ee-112">This argument represents the names of the computers to check and join.</span></span>

3. <span data-ttu-id="0e8ee-113">Erstellen Sie ein Argument mit dem Namen `DomainCred` des Typs [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="0e8ee-113">Create an argument named `DomainCred` of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="0e8ee-114">Dieses Argument stellt die Anmeldeinformationen für die Domäne für ein Domänenkonto an, die zum Hinzufügen eines Computers zur Domäne berechtigt ist.</span><span class="sxs-lookup"><span data-stu-id="0e8ee-114">This argument represents the domain credentials of a domain account that is authorized to join a computer to the domain.</span></span>

4. <span data-ttu-id="0e8ee-115">Erstellen Sie ein Argument mit dem Namen `MachineCred` des Typs [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span><span class="sxs-lookup"><span data-stu-id="0e8ee-115">Create an argument named `MachineCred` of type [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential).</span></span> <span data-ttu-id="0e8ee-116">Dieses Argument stellt die Anmeldeinformationen eines Administrators auf den Computern, um zu überprüfen und zu verknüpfen.</span><span class="sxs-lookup"><span data-stu-id="0e8ee-116">This argument represents the credentials of an administrator on the computers to check and join.</span></span>

5. <span data-ttu-id="0e8ee-117">Hinzufügen einer **ParallelForEach** Aktivität innerhalb der **Sequenz** Aktivität.</span><span class="sxs-lookup"><span data-stu-id="0e8ee-117">Add a **ParallelForEach** activity inside the **Sequence** activity.</span></span> <span data-ttu-id="0e8ee-118">Geben Sie `comp` und `ComputerName` in den Textfeldern, damit die Elemente die Schleife durchläuft die `ComputerName` Array.</span><span class="sxs-lookup"><span data-stu-id="0e8ee-118">Enter `comp` and `ComputerName` in the text boxes so that the loop iterates through the elements of the `ComputerName` array.</span></span>

6. <span data-ttu-id="0e8ee-119">Hinzufügen einer **Sequenz** Aktivität in den Text der der **ParallelForEach** Aktivität.</span><span class="sxs-lookup"><span data-stu-id="0e8ee-119">Add a **Sequence** activity to the body of the **ParallelForEach** activity.</span></span> <span data-ttu-id="0e8ee-120">Legen Sie die **"DisplayName"** Eigenschaft der Sequenz, die `JoinDomain`.</span><span class="sxs-lookup"><span data-stu-id="0e8ee-120">Set the **DisplayName** property of the sequence to `JoinDomain`.</span></span>

7. <span data-ttu-id="0e8ee-121">Hinzufügen einer **GetWmiObject** Aktivität, um die **JoinDomain** Sequenz.</span><span class="sxs-lookup"><span data-stu-id="0e8ee-121">Add a **GetWmiObject** activity to the **JoinDomain** sequence.</span></span>

8. <span data-ttu-id="0e8ee-122">Bearbeiten der Eigenschaften der **GetWmiObject** Aktivität wie folgt.</span><span class="sxs-lookup"><span data-stu-id="0e8ee-122">Edit the properties of the **GetWmiObject** activity as follows.</span></span>

   |<span data-ttu-id="0e8ee-123">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="0e8ee-123">Property</span></span>|<span data-ttu-id="0e8ee-124">Wert</span><span class="sxs-lookup"><span data-stu-id="0e8ee-124">Value</span></span>|
   |--------------|-----------|
   |<span data-ttu-id="0e8ee-125">**Klasse**</span><span class="sxs-lookup"><span data-stu-id="0e8ee-125">**Class**</span></span>|<span data-ttu-id="0e8ee-126">"Win32_ComputerSystem"</span><span class="sxs-lookup"><span data-stu-id="0e8ee-126">"Win32_ComputerSystem"</span></span>|
   |<span data-ttu-id="0e8ee-127">**PSComputerName**</span><span class="sxs-lookup"><span data-stu-id="0e8ee-127">**PSComputerName**</span></span>|<span data-ttu-id="0e8ee-128">{Comp}</span><span class="sxs-lookup"><span data-stu-id="0e8ee-128">{comp}</span></span>|
   |<span data-ttu-id="0e8ee-129">**PSCredential**</span><span class="sxs-lookup"><span data-stu-id="0e8ee-129">**PSCredential**</span></span>|<span data-ttu-id="0e8ee-130">MachineCred</span><span class="sxs-lookup"><span data-stu-id="0e8ee-130">MachineCred</span></span>|

9. <span data-ttu-id="0e8ee-131">Hinzufügen einer **AddComputer** Aktivität, um die **JoinDomain** nach dem Sequenzieren der **GetWmiObject** Aktivität.</span><span class="sxs-lookup"><span data-stu-id="0e8ee-131">Add an **AddComputer** activity to the **JoinDomain** sequence after the **GetWmiObject** activity.</span></span>

10. <span data-ttu-id="0e8ee-132">Bearbeiten der Eigenschaften der **AddComputer** Aktivität wie folgt.</span><span class="sxs-lookup"><span data-stu-id="0e8ee-132">Edit the properties of the **AddComputer** activity as follows.</span></span>

    |<span data-ttu-id="0e8ee-133">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="0e8ee-133">Property</span></span>|<span data-ttu-id="0e8ee-134">Wert</span><span class="sxs-lookup"><span data-stu-id="0e8ee-134">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="0e8ee-135">**ComputerName**</span><span class="sxs-lookup"><span data-stu-id="0e8ee-135">**ComputerName**</span></span>|<span data-ttu-id="0e8ee-136">{Comp}</span><span class="sxs-lookup"><span data-stu-id="0e8ee-136">{comp}</span></span>|
    |<span data-ttu-id="0e8ee-137">**DomainCredential**</span><span class="sxs-lookup"><span data-stu-id="0e8ee-137">**DomainCredential**</span></span>|<span data-ttu-id="0e8ee-138">DomainCred</span><span class="sxs-lookup"><span data-stu-id="0e8ee-138">DomainCred</span></span>|

11. <span data-ttu-id="0e8ee-139">Hinzufügen einer **RestartComputer** Aktivität, um die **JoinDomain** nach dem Sequenzieren der **AddComputer** Aktivität.</span><span class="sxs-lookup"><span data-stu-id="0e8ee-139">Add a **RestartComputer** activity to the **JoinDomain** sequence after the **AddComputer** activity.</span></span>

12. <span data-ttu-id="0e8ee-140">Bearbeiten der Eigenschaften der **RestartComputer** Aktivität wie folgt.</span><span class="sxs-lookup"><span data-stu-id="0e8ee-140">Edit the properties of the **RestartComputer** activity as follows.</span></span>

    |<span data-ttu-id="0e8ee-141">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="0e8ee-141">Property</span></span>|<span data-ttu-id="0e8ee-142">Wert</span><span class="sxs-lookup"><span data-stu-id="0e8ee-142">Value</span></span>|
    |--------------|-----------|
    |<span data-ttu-id="0e8ee-143">**ComputerName**</span><span class="sxs-lookup"><span data-stu-id="0e8ee-143">**ComputerName**</span></span>|<span data-ttu-id="0e8ee-144">{Comp}</span><span class="sxs-lookup"><span data-stu-id="0e8ee-144">{comp}</span></span>|
    |<span data-ttu-id="0e8ee-145">**Anmeldeinformationen**</span><span class="sxs-lookup"><span data-stu-id="0e8ee-145">**Credential**</span></span>|<span data-ttu-id="0e8ee-146">MachineCred</span><span class="sxs-lookup"><span data-stu-id="0e8ee-146">MachineCred</span></span>|
    |<span data-ttu-id="0e8ee-147">**für**</span><span class="sxs-lookup"><span data-stu-id="0e8ee-147">**For**</span></span>|<span data-ttu-id="0e8ee-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span><span class="sxs-lookup"><span data-stu-id="0e8ee-148">Microsoft.PowerShell.Commands.WaitForServiceTypes.PowerShell</span></span>|
    |<span data-ttu-id="0e8ee-149">**Force**</span><span class="sxs-lookup"><span data-stu-id="0e8ee-149">**Force**</span></span>|<span data-ttu-id="0e8ee-150">Wahr</span><span class="sxs-lookup"><span data-stu-id="0e8ee-150">True</span></span>|
    |<span data-ttu-id="0e8ee-151">Wartezeit</span><span class="sxs-lookup"><span data-stu-id="0e8ee-151">Wait</span></span>|<span data-ttu-id="0e8ee-152">Wahr</span><span class="sxs-lookup"><span data-stu-id="0e8ee-152">True</span></span>|
    |<span data-ttu-id="0e8ee-153">PSComputerName</span><span class="sxs-lookup"><span data-stu-id="0e8ee-153">PSComputerName</span></span>|<span data-ttu-id="0e8ee-154">{""}</span><span class="sxs-lookup"><span data-stu-id="0e8ee-154">{""}</span></span>|

13. <span data-ttu-id="0e8ee-155">Hinzufügen einer **GetWmiObject** Aktivität, um die **JoinDomain** nach dem Sequenzieren der **RestartComputer** Aktivität.</span><span class="sxs-lookup"><span data-stu-id="0e8ee-155">Add a **GetWmiObject** activity to the **JoinDomain** sequence after the **RestartComputer** activity.</span></span> <span data-ttu-id="0e8ee-156">Bearbeiten der Eigenschaften, um die vorherige entsprechen **GetWmiObject** Aktivität.</span><span class="sxs-lookup"><span data-stu-id="0e8ee-156">Edit its properties to be the same as the previous **GetWmiObject** activity.</span></span>

    <span data-ttu-id="0e8ee-157">Wenn Sie die Verfahren abgeschlossen haben, sollte das Workflow-Designer-Fenster wie folgt aussehen.</span><span class="sxs-lookup"><span data-stu-id="0e8ee-157">When you have finished the procedures, the workflow design window should look like this.</span></span>

    <span data-ttu-id="0e8ee-158">![JoinDomain XAML im Workflow-Designer](../media/joindomainworkflow.png)
    ![JoinDomain XAML im Workflow-Designer](../media/joindomainworkflow.png "JoinDomainWorkflow")</span><span class="sxs-lookup"><span data-stu-id="0e8ee-158">![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png)
![JoinDomain XAML in Workflow designer](../media/joindomainworkflow.png "JoinDomainWorkflow")</span></span>