---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: EnableDebugConfiguration-Methode
ms.openlocfilehash: f1290e4d898332361850ffc85aa0a8d79863c8f7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953437"
---
# <a name="enabledebugconfiguration-method"></a><span data-ttu-id="15c1f-103">EnableDebugConfiguration-Methode</span><span class="sxs-lookup"><span data-stu-id="15c1f-103">EnableDebugConfiguration method</span></span>

<span data-ttu-id="15c1f-104">Aktiviert das Debuggen von DSC-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="15c1f-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="15c1f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="15c1f-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="15c1f-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="15c1f-106">Parameters</span></span>

<span data-ttu-id="15c1f-107">*BreakAll* \[in\] Legt einen Haltepunkt in jeder Zeile im Ressourcenskript fest.</span><span class="sxs-lookup"><span data-stu-id="15c1f-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="15c1f-108">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="15c1f-108">Return value</span></span>

<span data-ttu-id="15c1f-109">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="15c1f-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="15c1f-110">Hinweise</span><span class="sxs-lookup"><span data-stu-id="15c1f-110">Remarks</span></span>

<span data-ttu-id="15c1f-111">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="15c1f-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="15c1f-112">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="15c1f-112">Requirements</span></span>

<span data-ttu-id="15c1f-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="15c1f-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="15c1f-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="15c1f-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="15c1f-115">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="15c1f-115">See also</span></span>

[<span data-ttu-id="15c1f-116">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="15c1f-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
