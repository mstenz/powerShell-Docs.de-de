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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364289"
---
# <a name="invoking-cmdlets-and-scripts-within-a-cmdlet"></a><span data-ttu-id="6875a-102">Aufrufen von Cmdlets und Skripts in einem Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6875a-102">Invoking Cmdlets and Scripts Within a Cmdlet</span></span>

<span data-ttu-id="6875a-103">Ein Cmdlet kann andere Cmdlets und Skripts in der Eingabe Verarbeitungsmethode des Cmdlets aufrufen.</span><span class="sxs-lookup"><span data-stu-id="6875a-103">A cmdlet can invoke other cmdlets and scripts from within the input processing method of the cmdlet.</span></span> <span data-ttu-id="6875a-104">Dies ermöglicht es Ihnen, die Funktionalität vorhandener Cmdlets und Skripts zum Cmdlet hinzuzufügen, ohne den Code neu schreiben zu müssen.</span><span class="sxs-lookup"><span data-stu-id="6875a-104">This allows you to add the functionality of existing cmdlets and scripts to your cmdlet without having to rewrite the code.</span></span>

## <a name="the-invoke-method"></a><span data-ttu-id="6875a-105">Die Invoke-Methode</span><span class="sxs-lookup"><span data-stu-id="6875a-105">The Invoke Method</span></span>

<span data-ttu-id="6875a-106">Alle Cmdlets können ein vorhandenes Cmdlet aufrufen, indem Sie die [System. Management. Automation. Cmdlet.](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) Call-Methode aus einer Eingabe Verarbeitungsmethode aufrufen, wie z [. b. System. Management. Automation. Cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), die vom Cmdlet überschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="6875a-106">All cmdlets can invoke an existing cmdlet by calling the [System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method from within an input processing method, such as [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), that is overridden by the cmdlet.</span></span> <span data-ttu-id="6875a-107">Sie können jedoch nur die Cmdlets aufrufen, die direkt von der [System. Management. Automation. Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) -Klasse abgeleitet werden.</span><span class="sxs-lookup"><span data-stu-id="6875a-107">However, you can invoke only those cmdlets that derive directly from the [System.Management.Automation.Cmdlet](/dotnet/api/System.Management.Automation.Cmdlet) class.</span></span> <span data-ttu-id="6875a-108">Sie können kein Cmdlet aufrufen, das von der [System. Management. Automation. PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) -Klasse abgeleitet wird.</span><span class="sxs-lookup"><span data-stu-id="6875a-108">You cannot invoke a cmdlet that derives from the [System.Management.Automation.PSCmdlet](/dotnet/api/System.Management.Automation.PSCmdlet) class.</span></span>

<span data-ttu-id="6875a-109">Die [System. Management. Automation. Cmdlet. aufrufen \*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) -Methode verfügt über die folgenden Varianten.</span><span class="sxs-lookup"><span data-stu-id="6875a-109">The [System.Management.Automation.Cmdlet.Invoke\*](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) method has the following variants.</span></span>

<span data-ttu-id="6875a-110">[System. Management. Automation. Cmdlet. aufrufen](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) diese Variante Ruft das Cmdlet-Objekt auf und gibt eine Auflistung von T-Objekten zurück.</span><span class="sxs-lookup"><span data-stu-id="6875a-110">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a collection of "T" type objects.</span></span>

<span data-ttu-id="6875a-111">[System. Management. Automation. Cmdlet. aufrufen](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) diese Variante Ruft das Cmdlet-Objekt auf und gibt einen stark typisierten emumerator zurück.</span><span class="sxs-lookup"><span data-stu-id="6875a-111">[System.Management.Automation.Cmdlet.Invoke](/dotnet/api/System.Management.Automation.Cmdlet.Invoke) This variant invokes the cmdlet object and returns a strongly typed emumerator.</span></span> <span data-ttu-id="6875a-112">Diese Variante ermöglicht dem Benutzer die Verwendung der Objekte in der Auflistung, um benutzerdefinierte Vorgänge auszuführen.</span><span class="sxs-lookup"><span data-stu-id="6875a-112">This variant allows the user to use the objects in the collection to perform custom operations.</span></span>

## <a name="examples"></a><span data-ttu-id="6875a-113">Beispiele</span><span class="sxs-lookup"><span data-stu-id="6875a-113">Examples</span></span>

|<span data-ttu-id="6875a-114">Beispiel</span><span class="sxs-lookup"><span data-stu-id="6875a-114">Example</span></span>|<span data-ttu-id="6875a-115">Description</span><span class="sxs-lookup"><span data-stu-id="6875a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6875a-116">Aufrufen von Cmdlets in einem Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6875a-116">Invoking Cmdlets Within a Cmdlet</span></span>](./how-to-invoke-a-cmdlet-from-within-a-cmdlet.md)|<span data-ttu-id="6875a-117">Dieses Beispiel zeigt, wie Sie ein Cmdlet in einem anderen Cmdlet aufrufen.</span><span class="sxs-lookup"><span data-stu-id="6875a-117">This example shows how to invoke a cmdlet from within another cmdlet.</span></span>|
|[<span data-ttu-id="6875a-118">Aufrufen von Skripts in einem Cmdlet</span><span class="sxs-lookup"><span data-stu-id="6875a-118">Invoking Scripts Within a Cmdlet</span></span>](./how-to-invoke-scripts-within-a-cmdlet.md)|<span data-ttu-id="6875a-119">In diesem Beispiel wird gezeigt, wie ein Skript aufgerufen wird, das für das Cmdlet aus einem anderen Cmdlet bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="6875a-119">This example shows how to invoke a script that is supplied to the cmdlet from within another cmdlet.</span></span>|

## <a name="see-also"></a><span data-ttu-id="6875a-120">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="6875a-120">See Also</span></span>

[<span data-ttu-id="6875a-121">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="6875a-121">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
