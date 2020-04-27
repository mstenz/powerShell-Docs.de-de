---
ms.date: 06/12/2017
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: EnableDebugConfiguration-Methode
ms.openlocfilehash: f1290e4d898332361850ffc85aa0a8d79863c8f7
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953437"
---
# <a name="enabledebugconfiguration-method"></a><span data-ttu-id="cdd39-103">EnableDebugConfiguration-Methode</span><span class="sxs-lookup"><span data-stu-id="cdd39-103">EnableDebugConfiguration method</span></span>

<span data-ttu-id="cdd39-104">Aktiviert das Debuggen von DSC-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="cdd39-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="cdd39-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="cdd39-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="cdd39-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="cdd39-106">Parameters</span></span>

<span data-ttu-id="cdd39-107">*BreakAll* \[in\] Legt einen Breakpoint in jeder Zeile im Ressourcenskript fest.</span><span class="sxs-lookup"><span data-stu-id="cdd39-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="cdd39-108">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="cdd39-108">Return value</span></span>

<span data-ttu-id="cdd39-109">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="cdd39-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="cdd39-110">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="cdd39-110">Remarks</span></span>

<span data-ttu-id="cdd39-111">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="cdd39-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="cdd39-112">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="cdd39-112">Requirements</span></span>

<span data-ttu-id="cdd39-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="cdd39-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="cdd39-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="cdd39-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="cdd39-115">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="cdd39-115">See also</span></span>

[<span data-ttu-id="cdd39-116">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="cdd39-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
