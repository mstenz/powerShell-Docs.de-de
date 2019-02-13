---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: RollBack-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 4956900ecd2c9cb7f2e2b5bcab94616f9f5d5565
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679363"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="bd095-103">RollBack-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="bd095-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="bd095-104">Führt einen Rollback der Konfiguration zu einer früheren Version durch.</span><span class="sxs-lookup"><span data-stu-id="bd095-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="bd095-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="bd095-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="bd095-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="bd095-106">Parameters</span></span>

<span data-ttu-id="bd095-107">*configurationNumber* \[in\] Gibt die angeforderte Konfiguration an.</span><span class="sxs-lookup"><span data-stu-id="bd095-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="bd095-108">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="bd095-108">Return value</span></span>

<span data-ttu-id="bd095-109">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="bd095-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="bd095-110">Hinweise</span><span class="sxs-lookup"><span data-stu-id="bd095-110">Remarks</span></span>

<span data-ttu-id="bd095-111">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="bd095-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bd095-112">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="bd095-112">Requirements</span></span>

<span data-ttu-id="bd095-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="bd095-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="bd095-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="bd095-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="bd095-115">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="bd095-115">See also</span></span>

[<span data-ttu-id="bd095-116">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="bd095-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)