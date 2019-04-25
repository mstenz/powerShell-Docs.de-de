---
title: Benutzern, die Bestätigung anfordern | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6f337498-c534-40ed-968a-09d4d9ca3849
caps.latest.revision: 8
ms.openlocfilehash: ed9ff9fc1668a89e1ac0ceac8f0800a15b349226
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067217"
---
# <a name="users-requesting-confirmation"></a><span data-ttu-id="1beaf-102">Anfordern der Bestätigung von Benutzern</span><span class="sxs-lookup"><span data-stu-id="1beaf-102">Users Requesting Confirmation</span></span>

<span data-ttu-id="1beaf-103">Wenn Sie den Wert angeben `true` für die `SupportsShouldProcess` der Deklaration der Cmdlet-Attribut angeben, der Benutzer können die `Confirm` Parameter an der Eingabeaufforderung.</span><span class="sxs-lookup"><span data-stu-id="1beaf-103">When you specify a value of `true` for the `SupportsShouldProcess` parameter of the Cmdlet attribute declaration, users can specify the `Confirm` parameter at the command prompt.</span></span>

<span data-ttu-id="1beaf-104">In der standardumgebung, Benutzer können angeben, die `Confirm` Parameter oder `"-Confirm:$true` , damit eine Bestätigung angefordert wird bei der [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) Methode wird aufgerufen.</span><span class="sxs-lookup"><span data-stu-id="1beaf-104">In the default environment, users can specify the `Confirm` parameter or `"-Confirm:$true` so that confirmation is requested when the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) method is called.</span></span> <span data-ttu-id="1beaf-105">Dadurch wird der [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) Bestätigung Benutzeranfragen, sogar mit schwerwiegenden Auswirkungen.</span><span class="sxs-lookup"><span data-stu-id="1beaf-105">This bypasses [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) confirmation requests, even for high-impact operations.</span></span>

<span data-ttu-id="1beaf-106">Wenn `Confirm` nicht angegeben ist, die [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) Aufruf fordert die Bestätigung, wenn die `$ConfirmPreference` Einstellungsvariable ist größer als oder gleich der `ConfirmImpact` festlegen, der die -Cmdlet oder Anbieter.</span><span class="sxs-lookup"><span data-stu-id="1beaf-106">If `Confirm` is not specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation if the `$ConfirmPreference` preference variable is equal to or greater than the `ConfirmImpact` setting of the cmdlet or provider.</span></span> <span data-ttu-id="1beaf-107">Die Standardeinstellung von `$ConfirmPreference` hoch.</span><span class="sxs-lookup"><span data-stu-id="1beaf-107">The default setting of `$ConfirmPreference` is High.</span></span> <span data-ttu-id="1beaf-108">Aus diesem Grund Bestätigung der Anfrage in der standardumgebung nur Cmdlets und Anbieter, die eine Aktion mit schwerwiegenden Auswirkungen festlegen.</span><span class="sxs-lookup"><span data-stu-id="1beaf-108">Therefore, in the default environment, only cmdlets and providers that specify a high-impact action request confirmation.</span></span>

<span data-ttu-id="1beaf-109">Wenn `Confirm` ist "false" oder, wenn `"-Confirm:$false` angegeben wird, die [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) Aufruf fordert eine Bestätigung vom Benutzer, und die `$ConfirmPreference` Shellvariable wird ignoriert.</span><span class="sxs-lookup"><span data-stu-id="1beaf-109">If `Confirm` is false or if `"-Confirm:$false` is specified, the [System.Management.Automation.Cmdlet.ShouldProcess](/dotnet/api/System.Management.Automation.Cmdlet.ShouldProcess) call requests confirmation from the user, and the `$ConfirmPreference` shell variable is ignored.</span></span>

## <a name="remarks"></a><span data-ttu-id="1beaf-110">Hinweise</span><span class="sxs-lookup"><span data-stu-id="1beaf-110">Remarks</span></span>

- <span data-ttu-id="1beaf-111">Für Cmdlets und Anbieter, die angeben, `SupportsShouldProcess`, aber nicht `ConfirmImpact`, diese Aktionen wie "mittleren Impact" Aktionen verarbeitet werden und sie werden nicht standardmäßig aufgefordert.</span><span class="sxs-lookup"><span data-stu-id="1beaf-111">For cmdlets and providers that specify `SupportsShouldProcess`, but not `ConfirmImpact`, those actions are handled as "medium impact" actions, and they will not prompt by default.</span></span> <span data-ttu-id="1beaf-112">Ihre Impact-Level ist kleiner als die Standardeinstellung für die `$ConfirmPreference` Einstellungsvariable.</span><span class="sxs-lookup"><span data-stu-id="1beaf-112">Their impact level is less than the default setting of the `$ConfirmPreference` preference variable.</span></span>

- <span data-ttu-id="1beaf-113">Wenn der Benutzer gibt die `Verbose` -Parameter werden des Vorgangs benachrichtigt werden, auch wenn sie nicht zur Bestätigung aufgefordert werden.</span><span class="sxs-lookup"><span data-stu-id="1beaf-113">If the user specifies the `Verbose` parameter, they will be notified of the operation even if they are not prompted for confirmation.</span></span>

## <a name="see-also"></a><span data-ttu-id="1beaf-114">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="1beaf-114">See Also</span></span>

[<span data-ttu-id="1beaf-115">Schreiben eines Windows PowerShell-Cmdlets</span><span class="sxs-lookup"><span data-stu-id="1beaf-115">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
