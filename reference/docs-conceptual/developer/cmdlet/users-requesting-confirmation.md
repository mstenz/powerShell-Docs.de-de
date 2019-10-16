---
title: Benutzer, die eine Bestätigung anfordern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f337498-c534-40ed-968a-09d4d9ca3849
caps.latest.revision: 8
ms.openlocfilehash: ed9ff9fc1668a89e1ac0ceac8f0800a15b349226
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369249"
---
# <a name="users-requesting-confirmation"></a><span data-ttu-id="044e3-102">Anfordern der Bestätigung von Benutzern</span><span class="sxs-lookup"><span data-stu-id="044e3-102">Users Requesting Confirmation</span></span>

<span data-ttu-id="044e3-103">Wenn Sie für den `SupportsShouldProcess`-Parameter der Cmdlet-Attribut Deklaration den Wert `true` angeben, können Benutzer den `Confirm`-Parameter an der Eingabeaufforderung angeben.</span><span class="sxs-lookup"><span data-stu-id="044e3-103">When you specify a value of `true` for the `SupportsShouldProcess` parameter of the Cmdlet attribute declaration, users can specify the `Confirm` parameter at the command prompt.</span></span>

<span data-ttu-id="044e3-104">In der Standardumgebung können Benutzer den `Confirm`-Parameter oder `"-Confirm:$true` angeben, damit die Bestätigung angefordert wird, wenn die [System. Management. Automation. Cmdlet. tiondprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Methode aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="044e3-104">In the default environment, users can specify the `Confirm` parameter or `"-Confirm:$true` so that confirmation is requested when the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method is called.</span></span> <span data-ttu-id="044e3-105">Dies umgeht [System. Management. Automation. Cmdlet. tiondprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Bestätigungs Anforderungen, auch für Vorgänge mit hohen Auswirkungen.</span><span class="sxs-lookup"><span data-stu-id="044e3-105">This bypasses [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) confirmation requests, even for high-impact operations.</span></span>

<span data-ttu-id="044e3-106">Wenn `Confirm` nicht angegeben wird, fordert der [System. Management. Automation. Cmdlet. tiondprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Befehl eine Bestätigung an, wenn die `$ConfirmPreference`-Einstellungs Variable größer oder gleich der `ConfirmImpact`-Einstellung des Cmdlets oder Anbieters ist.</span><span class="sxs-lookup"><span data-stu-id="044e3-106">If `Confirm` is not specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation if the `$ConfirmPreference` preference variable is equal to or greater than the `ConfirmImpact` setting of the cmdlet or provider.</span></span> <span data-ttu-id="044e3-107">Die Standardeinstellung `$ConfirmPreference` ist hoch.</span><span class="sxs-lookup"><span data-stu-id="044e3-107">The default setting of `$ConfirmPreference` is High.</span></span> <span data-ttu-id="044e3-108">In der Standardumgebung gibt es daher nur Cmdlets und Anbieter, die eine Bestätigungs-Aktions Anforderungs Bestätigung angeben.</span><span class="sxs-lookup"><span data-stu-id="044e3-108">Therefore, in the default environment, only cmdlets and providers that specify a high-impact action request confirmation.</span></span>

<span data-ttu-id="044e3-109">Wenn `Confirm` false ist oder `"-Confirm:$false` angegeben ist, fordert der [System. Management. Automation. Cmdlet. tiondprocess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) -Befehl eine Bestätigung vom Benutzer an, und die `$ConfirmPreference`-Shellvariable wird ignoriert.</span><span class="sxs-lookup"><span data-stu-id="044e3-109">If `Confirm` is false or if `"-Confirm:$false` is specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation from the user, and the `$ConfirmPreference` shell variable is ignored.</span></span>

## <a name="remarks"></a><span data-ttu-id="044e3-110">Hinweise</span><span class="sxs-lookup"><span data-stu-id="044e3-110">Remarks</span></span>

- <span data-ttu-id="044e3-111">Für Cmdlets und Anbieter, die `SupportsShouldProcess` angeben, jedoch nicht `ConfirmImpact`, werden diese Aktionen als "mittlere Auswirkung"-Aktionen behandelt, und Sie werden nicht standardmäßig aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="044e3-111">For cmdlets and providers that specify `SupportsShouldProcess`, but not `ConfirmImpact`, those actions are handled as "medium impact" actions, and they will not prompt by default.</span></span> <span data-ttu-id="044e3-112">Die Auswirkungs Stufe ist kleiner als die Standardeinstellung der `$ConfirmPreference`-Einstellungs Variablen.</span><span class="sxs-lookup"><span data-stu-id="044e3-112">Their impact level is less than the default setting of the `$ConfirmPreference` preference variable.</span></span>

- <span data-ttu-id="044e3-113">Wenn der Benutzer den `Verbose`-Parameter angibt, wird er über den Vorgang benachrichtigt, auch wenn er nicht zur Bestätigung aufgefordert wird.</span><span class="sxs-lookup"><span data-stu-id="044e3-113">If the user specifies the `Verbose` parameter, they will be notified of the operation even if they are not prompted for confirmation.</span></span>

## <a name="see-also"></a><span data-ttu-id="044e3-114">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="044e3-114">See Also</span></span>

[<span data-ttu-id="044e3-115">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="044e3-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
