---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: EnableDebugConfiguration-Methode
ms.openlocfilehash: f1290e4d898332361850ffc85aa0a8d79863c8f7
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727153"
---
# <a name="enabledebugconfiguration-method"></a><span data-ttu-id="9bf28-103">EnableDebugConfiguration-Methode</span><span class="sxs-lookup"><span data-stu-id="9bf28-103">EnableDebugConfiguration method</span></span>

<span data-ttu-id="9bf28-104">Aktiviert das Debuggen von DSC-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="9bf28-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="9bf28-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9bf28-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="9bf28-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="9bf28-106">Parameters</span></span>

<span data-ttu-id="9bf28-107">*BreakAll* \[in\] Legt einen Haltepunkt in jeder Zeile im Ressourcenskript fest.</span><span class="sxs-lookup"><span data-stu-id="9bf28-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="9bf28-108">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="9bf28-108">Return value</span></span>

<span data-ttu-id="9bf28-109">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="9bf28-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9bf28-110">Hinweise</span><span class="sxs-lookup"><span data-stu-id="9bf28-110">Remarks</span></span>

<span data-ttu-id="9bf28-111">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="9bf28-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9bf28-112">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="9bf28-112">Requirements</span></span>

<span data-ttu-id="9bf28-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9bf28-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="9bf28-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9bf28-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="9bf28-115">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="9bf28-115">See also</span></span>

[<span data-ttu-id="9bf28-116">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="9bf28-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
