---
title: 'Vorgehensweise: Erstellen Sie ein Windows PowerShell-Snap-in | Microsoft-Dokumentation'
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
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055936"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a><span data-ttu-id="fd09e-102">Erstellen eines Windows PowerShell-Snap-Ins</span><span class="sxs-lookup"><span data-stu-id="fd09e-102">How to Create a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="fd09e-103">Ein Windows PowerShell-Snap-in die bietet eines Mechanismus zum Registrieren von Sätze von Cmdlets und eine andere Windows PowerShell-Anbieter mit der Shell, daher zum Erweitern der Funktionalität der Shell aus.</span><span class="sxs-lookup"><span data-stu-id="fd09e-103">A Windows PowerShell snap-in provides a mechanism for registering sets of cmdlets and another Windows PowerShell provider with the shell, thus extending the functionality of the shell.</span></span> <span data-ttu-id="fd09e-104">Ein Windows PowerShell-Snap-in kann die Cmdlets und Anbieter in einer einzelnen Assembly registrieren, oder sie können eine bestimmte Liste von Cmdlets und Anbieter.</span><span class="sxs-lookup"><span data-stu-id="fd09e-104">A Windows PowerShell snap-in can register all the cmdlets and providers in a single assembly, or it can register a specific list of cmdlets and providers.</span></span>

<span data-ttu-id="fd09e-105">-Snap-in Assemblys sollten in einem geschützten Verzeichnis installiert werden, wie sie mit anderen Betriebssystemen wäre.</span><span class="sxs-lookup"><span data-stu-id="fd09e-105">Snap-in assemblies should be installed in a protected directory, just as they would be with other operating systems.</span></span> <span data-ttu-id="fd09e-106">Andernfalls können böswillige Benutzer eine Assembly mit unsicherem Code ersetzen.</span><span class="sxs-lookup"><span data-stu-id="fd09e-106">Otherwise, malicious users can replace an assembly with unsafe code.</span></span>

## <a name="windows-powershell-snap-in-classes"></a><span data-ttu-id="fd09e-107">Windows PowerShell-Snap-in Klassen</span><span class="sxs-lookup"><span data-stu-id="fd09e-107">Windows PowerShell Snap-in Classes</span></span>

<span data-ttu-id="fd09e-108">Alle Windows PowerShell-Snap-in Klassen leiten sich von der [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) oder [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) Klassen.</span><span class="sxs-lookup"><span data-stu-id="fd09e-108">All Windows PowerShell snap-in classes derive from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) or [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classes.</span></span>

## <a name="examples"></a><span data-ttu-id="fd09e-109">Beispiele</span><span class="sxs-lookup"><span data-stu-id="fd09e-109">Examples</span></span>

<span data-ttu-id="fd09e-110">[Schreiben ein Windows PowerShell-Snap-in](./writing-a-windows-powershell-snap-in.md): Dieses Beispiel zeigt, wie Sie ein Snap-in erstellen, die verwendet wird, um alle Cmdlets und Anbieter in einer Assembly zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="fd09e-110">[Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md): This example shows how to create a snap-in that is used to register all the cmdlets and providers in an assembly.</span></span>

<span data-ttu-id="fd09e-111">[Schreiben ein benutzerdefiniertes Windows PowerShell-Snap-in](./writing-a-custom-windows-powershell-snap-in.md): Dieses Beispiel zeigt, wie Sie eine benutzerdefinierte-Snap-in erstellen, die verwendet wird, um einen bestimmten Satz von Cmdlets und Anbieter, die nicht existiert oder in einer einzelnen Assembly zu registrieren.</span><span class="sxs-lookup"><span data-stu-id="fd09e-111">[Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md): This example shows how to create a custom snap-in that is used to register a specific set of cmdlets and providers that might or might not exist in a single assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="fd09e-112">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="fd09e-112">See Also</span></span>

[<span data-ttu-id="fd09e-113">System.Management.Automation.PSSnapIn</span><span class="sxs-lookup"><span data-stu-id="fd09e-113">System.Management.Automation.PSSnapIn</span></span>](/dotnet/api/System.Management.Automation.PSSnapIn)

[<span data-ttu-id="fd09e-114">System.Management.Automation.Custompssnapin</span><span class="sxs-lookup"><span data-stu-id="fd09e-114">System.Management.Automation.Custompssnapin</span></span>](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[<span data-ttu-id="fd09e-115">Registrierung der Cmdlets</span><span class="sxs-lookup"><span data-stu-id="fd09e-115">Registering Cmdlets</span></span>](./registering-cmdlets.md)

[<span data-ttu-id="fd09e-116">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="fd09e-116">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
