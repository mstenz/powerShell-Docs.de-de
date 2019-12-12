---
title: Windows PowerShell-Konzepte | Microsoft-Dokumentation
ms.custom: ''
ms.date: 6/12/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3dd5608e-50b6-4c6a-aee3-dde0e86032bc
caps.latest.revision: 7
ms.openlocfilehash: 4410b1f9c80afefd5479fa68154f9947b805edcf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366679"
---
# <a name="windows-powershell-concepts"></a><span data-ttu-id="695fa-102">Windows PowerShell: Konzepte</span><span class="sxs-lookup"><span data-stu-id="695fa-102">Windows PowerShell Concepts</span></span>

<span data-ttu-id="695fa-103">Dieser Abschnitt enthält konzeptionelle Informationen, die Ihnen helfen, PowerShell aus der Sicht eines Entwicklers zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="695fa-103">This section contains conceptual information that will help you understand PowerShell from a developer's viewpoint.</span></span>

|<span data-ttu-id="695fa-104">Themenname</span><span class="sxs-lookup"><span data-stu-id="695fa-104">Topic Name</span></span>|<span data-ttu-id="695fa-105">Description</span><span class="sxs-lookup"><span data-stu-id="695fa-105">Description</span></span>|
|----------------|-----------------|
|[<span data-ttu-id="695fa-106">about_Objects</span><span class="sxs-lookup"><span data-stu-id="695fa-106">about_Objects</span></span>](/powershell/module/microsoft.powershell.core/about/about_objects)|<span data-ttu-id="695fa-107">Beschreibung von PowerShell-Objekten.</span><span class="sxs-lookup"><span data-stu-id="695fa-107">Description of PowerShell objects.</span></span> <span data-ttu-id="695fa-108">Weitere Informationen finden Sie unter Informationen [zur Objekt Erstellung](/powershell/module/microsoft.powershell.core/about/about_object_creation)</span><span class="sxs-lookup"><span data-stu-id="695fa-108">For more information, see [About Object Creation](/powershell/module/microsoft.powershell.core/about/about_object_creation)</span></span>|
|[<span data-ttu-id="695fa-109">Erstellen von Runspaces</span><span class="sxs-lookup"><span data-stu-id="695fa-109">Creating Runspaces</span></span>](../hosting/creating-runspaces.md)|<span data-ttu-id="695fa-110">Die Betriebsumgebungen, in denen Befehle verarbeitet werden.</span><span class="sxs-lookup"><span data-stu-id="695fa-110">The operating environments where commands are processed.</span></span> <span data-ttu-id="695fa-111">Weitere Informationen finden Sie unter [Runspace-Klasse](/dotnet/api/system.management.automation.runspaces.runspace).</span><span class="sxs-lookup"><span data-stu-id="695fa-111">For more information, see [Runspace Class](/dotnet/api/system.management.automation.runspaces.runspace).</span></span>|
|[<span data-ttu-id="695fa-112">Erweitern von Ausgabe Objekten</span><span class="sxs-lookup"><span data-stu-id="695fa-112">Extending Output Objects</span></span>](../cmdlet/extending-output-objects.md)|<span data-ttu-id="695fa-113">Erweitern von PowerShell-Objekten</span><span class="sxs-lookup"><span data-stu-id="695fa-113">How to extend PowerShell objects.</span></span> <span data-ttu-id="695fa-114">Weitere Informationen finden Sie unter Informationen [zu Typen. ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)</span><span class="sxs-lookup"><span data-stu-id="695fa-114">For more information, see [About Types.ps1xml](/powershell/module/microsoft.powershell.core/about/about_types.ps1xml)</span></span>|
|[<span data-ttu-id="695fa-115">Cmdlets werden registriert</span><span class="sxs-lookup"><span data-stu-id="695fa-115">Registering Cmdlets</span></span>](../cmdlet/registering-cmdlets.md)|<span data-ttu-id="695fa-116">Informationen zum verfügbar machen von Modulen und Snap-Ins in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="695fa-116">How to make modules and snap-ins available in PowerShell.</span></span> <span data-ttu-id="695fa-117">Weitere Informationen finden Sie unter [Module und Snap-Ins](../cmdlet/modules-and-snap-ins.md).</span><span class="sxs-lookup"><span data-stu-id="695fa-117">For more information, see [Modules and Snap-ins](../cmdlet/modules-and-snap-ins.md).</span></span>|
|[<span data-ttu-id="695fa-118">Anfordern der Bestätigung von Cmdlets</span><span class="sxs-lookup"><span data-stu-id="695fa-118">Requesting Confirmation from Cmdlets</span></span>](../cmdlet/requesting-confirmation-from-cmdlets.md)|<span data-ttu-id="695fa-119">Gibt an, wie Cmdlets und Anbieter Feedback vom Benutzer anfordern, bevor eine Aktion durchgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="695fa-119">How cmdlets and providers request feedback from the user before an action is taken.</span></span>|
|[<span data-ttu-id="695fa-120">Runtimedefinedparameter-Klasse</span><span class="sxs-lookup"><span data-stu-id="695fa-120">RuntimeDefinedParameter Class</span></span>](/dotnet/api/system.management.automation.runtimedefinedparameter)|<span data-ttu-id="695fa-121">Lauf Zeitparameter Deklarationen.</span><span class="sxs-lookup"><span data-stu-id="695fa-121">Runtime parameter declarations.</span></span>|
|[<span data-ttu-id="695fa-122">System. Management. Automation-Namespace</span><span class="sxs-lookup"><span data-stu-id="695fa-122">System.Management.Automation Namespace</span></span>](/dotnet/api/System.Management.Automation)|<span data-ttu-id="695fa-123">Übersicht über PowerShell-API-Namespaces.</span><span class="sxs-lookup"><span data-stu-id="695fa-123">Overview of PowerShell API namespaces.</span></span>|
|[<span data-ttu-id="695fa-124">Windows PowerShell-Anbieter (Übersicht)</span><span class="sxs-lookup"><span data-stu-id="695fa-124">Windows PowerShell Provider Overview</span></span>](../provider/windows-powershell-provider-overview.md)|<span data-ttu-id="695fa-125">Übersicht über PowerShell-Anbieter, die für den Zugriff auf Datenspeicher verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="695fa-125">Overview about PowerShell providers that are used to access data stores.</span></span>|
|[<span data-ttu-id="695fa-126">Schreiben von Hilfe für PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="695fa-126">Writing Help for PowerShell Cmdlets</span></span>](../help/writing-help-for-windows-powershell-cmdlets.md)|<span data-ttu-id="695fa-127">Informationen zum Schreiben von PowerShell-Cmdlet-Hilfe.</span><span class="sxs-lookup"><span data-stu-id="695fa-127">How to write PowerShell cmdlet Help.</span></span>|

## <a name="see-also"></a><span data-ttu-id="695fa-128">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="695fa-128">See also</span></span>

[<span data-ttu-id="695fa-129">PowerShell-Klasse</span><span class="sxs-lookup"><span data-stu-id="695fa-129">PowerShell Class</span></span>](/dotnet/api/system.management.automation.powershell)

[<span data-ttu-id="695fa-130">Referenz zur PowerShell-Kern-API</span><span class="sxs-lookup"><span data-stu-id="695fa-130">PowerShell Core API Reference</span></span>](/dotnet/api/?view=pscore-6.2.0)

[<span data-ttu-id="695fa-131">Windows PowerShell-Programmier Handbuch</span><span class="sxs-lookup"><span data-stu-id="695fa-131">Windows PowerShell Programmer's Guide</span></span>](windows-powershell-programmer-s-guide.md)

[<span data-ttu-id="695fa-132">Schreiben von Hilfe für Windows PowerShell-Module</span><span class="sxs-lookup"><span data-stu-id="695fa-132">Writing Help for Windows PowerShell Modules</span></span>](../module/writing-help-for-windows-powershell-modules.md)

[<span data-ttu-id="695fa-133">Schreiben eines Windows PowerShell-Anbieters</span><span class="sxs-lookup"><span data-stu-id="695fa-133">Writing a Windows Powershell Provider</span></span>](../provider/writing-a-windows-powershell-provider.md)

[<span data-ttu-id="695fa-134">Windows PowerShell-API-Referenz</span><span class="sxs-lookup"><span data-stu-id="695fa-134">Windows PowerShell API Reference</span></span>](/dotnet/api/?view=powershellsdk-1.1.0)

[<span data-ttu-id="695fa-135">Windows PowerShell-Referenz</span><span class="sxs-lookup"><span data-stu-id="695fa-135">Windows PowerShell Reference</span></span>](../windows-powershell-reference.md)