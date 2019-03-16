---
title: Aufrufen von Cmdlets und Skripts in einem Cmdlet | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7040a5c-4a47-42df-a2ea-96b134a4ed9b
caps.latest.revision: 10
ms.openlocfilehash: f20708ff41d9a6de90090997a875ba5371eccd74
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058877"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a><span data-ttu-id="41b63-102">Aufrufen von Cmdlets und Skripts in einem Cmdlet</span><span class="sxs-lookup"><span data-stu-id="41b63-102">Invoking Cmdlets and Scripts Within a Cmdlet</span></span>

<span data-ttu-id="41b63-103">Ein Cmdlet kann andere Cmdlets und Skripts in der Eingabe Verarbeitungsmethode des-Cmdlets aufrufen.</span><span class="sxs-lookup"><span data-stu-id="41b63-103">A cmdlet can invoke other cmdlets and scripts from within the input processing method of the cmdlet.</span></span> <span data-ttu-id="41b63-104">Dadurch können Sie Ihr Cmdlet die Funktionalität von vorhandenen Cmdlets und Skripts hinzuzufügen, ohne den Code umschreiben zu müssen.</span><span class="sxs-lookup"><span data-stu-id="41b63-104">This allows you to add the functionality of existing cmdlets and scripts to your cmdlet without having to rewrite the code.</span></span>

## <a name="the-invoke-method"></a><span data-ttu-id="41b63-105">Die Invoke-Methode</span><span class="sxs-lookup"><span data-stu-id="41b63-105">The Invoke Method</span></span>

<span data-ttu-id="41b63-106">Alle Cmdlets können ein vorhandenes Cmdlet aufrufen, durch den Aufruf der [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) Methode innerhalb einer eingabeverarbeitungsmethode, z. B. [ System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), d. h. außer Kraft gesetzt, indem Sie das Cmdlet.</span><span class="sxs-lookup"><span data-stu-id="41b63-106">All cmdlets can invoke an existing cmdlet by calling the [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method from within an input processing method, such as [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), that is overridden by the cmdlet.</span></span> <span data-ttu-id="41b63-107">Sie können jedoch nur die Cmdlets, die direkt vom abgeleitet sind Aufrufen der [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) Klasse.</span><span class="sxs-lookup"><span data-stu-id="41b63-107">However, you can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="41b63-108">Sie können nicht aufgerufen werden ein Cmdlet, das von abgeleitet ist die [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) Klasse.</span><span class="sxs-lookup"><span data-stu-id="41b63-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

<span data-ttu-id="41b63-109">Die [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) Methode hat die folgenden Varianten.</span><span class="sxs-lookup"><span data-stu-id="41b63-109">The [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method has the following variants.</span></span>

<span data-ttu-id="41b63-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) diese Variante der Cmdlet-Objekt aufruft, und gibt eine Auflistung von "T"-Type-Objekten.</span><span class="sxs-lookup"><span data-stu-id="41b63-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a collection of "T" type objects.</span></span>

<span data-ttu-id="41b63-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) diese Variante ruft stattdessen das Cmdlet auf und gibt eine stark typisierte Emumerator.</span><span class="sxs-lookup"><span data-stu-id="41b63-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a strongly typed emumerator.</span></span> <span data-ttu-id="41b63-112">Diese Variante kann der Benutzer die Objekte in der Auflistung zu verwenden, um benutzerdefinierte Vorgänge auszuführen.</span><span class="sxs-lookup"><span data-stu-id="41b63-112">This variant allows the user to use the objects in the collection to perform custom operations.</span></span>

## <a name="examples"></a><span data-ttu-id="41b63-113">Beispiele</span><span class="sxs-lookup"><span data-stu-id="41b63-113">Examples</span></span>

|<span data-ttu-id="41b63-114">Beispiel</span><span class="sxs-lookup"><span data-stu-id="41b63-114">Example</span></span>|<span data-ttu-id="41b63-115">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="41b63-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="41b63-116">Aufrufen des Cmdlets in einem Cmdlet</span><span class="sxs-lookup"><span data-stu-id="41b63-116">Invoking Cmdlets Within a Cmdlet</span></span>](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|<span data-ttu-id="41b63-117">Dieses Beispiel zeigt, wie ein Cmdlet in ein anderes Cmdlet aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="41b63-117">This example shows how to invoke a cmdlet from within another cmdlet.</span></span>|
|[<span data-ttu-id="41b63-118">Aufrufen von Skripts in einem Cmdlet</span><span class="sxs-lookup"><span data-stu-id="41b63-118">Invoking Scripts Within a Cmdlet</span></span>](./how-to-invoke-scripts-within-a-cmdlet.md)|<span data-ttu-id="41b63-119">Dieses Beispiel zeigt, wie Sie ein Skript aufrufen, die an das Cmdlet aus, in ein anderes Cmdlet bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="41b63-119">This example shows how to invoke a script that is supplied to the cmdlet from within another cmdlet.</span></span>|

## <a name="see-also"></a><span data-ttu-id="41b63-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="41b63-120">See Also</span></span>

[<span data-ttu-id="41b63-121">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="41b63-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
