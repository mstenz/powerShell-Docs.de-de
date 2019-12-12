---
title: Erstellen eines Windows PowerShell-Snap-Ins | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], examples
ms.assetid: 71bd9b2c-5f2e-4aa8-b5fe-08c956540d37
caps.latest.revision: 10
ms.openlocfilehash: 43199544dc02ccae4b61053c30d6ed36576adfcf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364429"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a><span data-ttu-id="cc494-102">Erstellen eines Windows PowerShell-Snap-Ins</span><span class="sxs-lookup"><span data-stu-id="cc494-102">How to Create a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="cc494-103">Ein Windows PowerShell-Snap-in bietet einen Mechanismus zum Registrieren von Cmdlets-Sätzen und eines anderen Windows PowerShell-Anbieters mit der Shell und erweitert so die Funktionalität der Shell.</span><span class="sxs-lookup"><span data-stu-id="cc494-103">A Windows PowerShell snap-in provides a mechanism for registering sets of cmdlets and another Windows PowerShell provider with the shell, thus extending the functionality of the shell.</span></span> <span data-ttu-id="cc494-104">Mit einem Windows PowerShell-Snap-in können alle Cmdlets und Anbieter in einer einzelnen Assembly registriert werden, oder es kann eine bestimmte Liste von Cmdlets und Anbietern registriert werden.</span><span class="sxs-lookup"><span data-stu-id="cc494-104">A Windows PowerShell snap-in can register all the cmdlets and providers in a single assembly, or it can register a specific list of cmdlets and providers.</span></span>

<span data-ttu-id="cc494-105">Snap-in-Assemblys sollten in einem geschützten Verzeichnis installiert werden, genauso wie bei anderen Betriebssystemen.</span><span class="sxs-lookup"><span data-stu-id="cc494-105">Snap-in assemblies should be installed in a protected directory, just as they would be with other operating systems.</span></span> <span data-ttu-id="cc494-106">Andernfalls können böswillige Benutzer eine Assembly durch unsicheren Code ersetzen.</span><span class="sxs-lookup"><span data-stu-id="cc494-106">Otherwise, malicious users can replace an assembly with unsafe code.</span></span>

## <a name="windows-powershell-snap-in-classes"></a><span data-ttu-id="cc494-107">Windows PowerShell-Snap-in-Klassen</span><span class="sxs-lookup"><span data-stu-id="cc494-107">Windows PowerShell Snap-in Classes</span></span>

<span data-ttu-id="cc494-108">Alle Windows PowerShell-Snap-in-Klassen werden von der [System. Management. Automation. PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) -Klasse oder der [System. Management. Automation. CustomPSSnapIn](/dotnet/api/System.Management.Automation.CustomPSSnapIn) -Klasse abgeleitet.</span><span class="sxs-lookup"><span data-stu-id="cc494-108">All Windows PowerShell snap-in classes derive from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) or [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classes.</span></span>

## <a name="examples"></a><span data-ttu-id="cc494-109">Beispiele</span><span class="sxs-lookup"><span data-stu-id="cc494-109">Examples</span></span>

<span data-ttu-id="cc494-110">[Schreiben eines Windows PowerShell-Snap-Ins](./writing-a-windows-powershell-snap-in.md): in diesem Beispiel wird gezeigt, wie ein Snap-in erstellt wird, das zum Registrieren aller Cmdlets und Anbieter in einer Assembly verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="cc494-110">[Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md): This example shows how to create a snap-in that is used to register all the cmdlets and providers in an assembly.</span></span>

<span data-ttu-id="cc494-111">[Schreiben eines benutzerdefinierten Windows PowerShell-Snap-Ins](./writing-a-custom-windows-powershell-snap-in.md): in diesem Beispiel wird gezeigt, wie ein benutzerdefiniertes Snap-in erstellt wird, das zum Registrieren eines bestimmten Satzes von Cmdlets und Anbietern verwendet wird, die in einer einzelnen Assembly vorhanden sein könnten oder nicht.</span><span class="sxs-lookup"><span data-stu-id="cc494-111">[Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md): This example shows how to create a custom snap-in that is used to register a specific set of cmdlets and providers that might or might not exist in a single assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="cc494-112">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="cc494-112">See Also</span></span>

[<span data-ttu-id="cc494-113">System. Management. Automation. PSSnapIn</span><span class="sxs-lookup"><span data-stu-id="cc494-113">System.Management.Automation.PSSnapIn</span></span>](/dotnet/api/System.Management.Automation.PSSnapIn)

[<span data-ttu-id="cc494-114">System. Management. Automation. CustomPSSnapIn</span><span class="sxs-lookup"><span data-stu-id="cc494-114">System.Management.Automation.Custompssnapin</span></span>](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[<span data-ttu-id="cc494-115">Cmdlets werden registriert</span><span class="sxs-lookup"><span data-stu-id="cc494-115">Registering Cmdlets</span></span>](./registering-cmdlets.md)

[<span data-ttu-id="cc494-116">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="cc494-116">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
