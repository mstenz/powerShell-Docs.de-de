---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: RollBack-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: c0a801c4037921e700e447d1434e246df0a63a4f
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="69425-103">RollBack-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="69425-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="69425-104">Führt einen Rollback der Konfiguration zu einer früheren Version durch.</span><span class="sxs-lookup"><span data-stu-id="69425-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="69425-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="69425-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="69425-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="69425-106">Parameters</span></span>
----------

<span data-ttu-id="69425-107">*configurationNumber* \[in\] Gibt die angeforderte Konfiguration an.</span><span class="sxs-lookup"><span data-stu-id="69425-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="69425-108">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="69425-108">Return value</span></span>
------------

<span data-ttu-id="69425-109">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="69425-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="69425-110">Hinweise</span><span class="sxs-lookup"><span data-stu-id="69425-110">Remarks</span></span>

<span data-ttu-id="69425-111">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="69425-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="69425-112">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="69425-112">Requirements</span></span>
------------
><span data-ttu-id="69425-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="69425-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="69425-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="69425-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="69425-115">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="69425-115">See also</span></span>


[<span data-ttu-id="69425-116">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="69425-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)