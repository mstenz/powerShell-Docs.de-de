---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: EnableDebugConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: b2eaebfa901cb5d93fd0183287073e6b31f975d1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55678008"
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="8cb1f-103">EnableDebugConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="8cb1f-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="8cb1f-104">Aktiviert das Debuggen von DSC-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="8cb1f-104">Enables DSC resource debugging.</span></span>

## <a name="syntax"></a><span data-ttu-id="8cb1f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8cb1f-105">Syntax</span></span>

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a><span data-ttu-id="8cb1f-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="8cb1f-106">Parameters</span></span>

<span data-ttu-id="8cb1f-107">*BreakAll* \[in\] Legt einen Haltepunkt in jeder Zeile im Ressourcenskript fest.</span><span class="sxs-lookup"><span data-stu-id="8cb1f-107">*BreakAll* \[in\] Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="8cb1f-108">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="8cb1f-108">Return value</span></span>

<span data-ttu-id="8cb1f-109">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="8cb1f-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8cb1f-110">Hinweise</span><span class="sxs-lookup"><span data-stu-id="8cb1f-110">Remarks</span></span>

<span data-ttu-id="8cb1f-111">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="8cb1f-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8cb1f-112">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="8cb1f-112">Requirements</span></span>

<span data-ttu-id="8cb1f-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="8cb1f-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="8cb1f-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="8cb1f-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="8cb1f-115">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="8cb1f-115">See also</span></span>

[<span data-ttu-id="8cb1f-116">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="8cb1f-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)