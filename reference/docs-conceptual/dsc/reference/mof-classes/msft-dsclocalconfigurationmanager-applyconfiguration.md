---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: ApplyConfiguration-Methode
ms.openlocfilehash: 0425b9a7db37e421830ba37da8f5c0a4877a1b72
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953457"
---
# <a name="applyconfiguration-method"></a><span data-ttu-id="d8ff5-103">ApplyConfiguration-Methode</span><span class="sxs-lookup"><span data-stu-id="d8ff5-103">ApplyConfiguration method</span></span>

<span data-ttu-id="d8ff5-104">Verwendet den Konfigurations-Agent, um die ausstehende Konfiguration anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="d8ff5-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="d8ff5-105">Wenn keine ausstehende Konfiguration vorhanden ist, wendet diese Methode die aktuelle Konfiguration erneut an.</span><span class="sxs-lookup"><span data-stu-id="d8ff5-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="d8ff5-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d8ff5-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="d8ff5-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="d8ff5-107">Parameters</span></span>

<span data-ttu-id="d8ff5-108">*force* \[in\] Wenn dies **true** ist, wird die aktuelle Konfiguration erneut angewendet, selbst wenn eine Konfiguration aussteht.</span><span class="sxs-lookup"><span data-stu-id="d8ff5-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="d8ff5-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="d8ff5-109">Return value</span></span>

<span data-ttu-id="d8ff5-110">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="d8ff5-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d8ff5-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="d8ff5-111">Remarks</span></span>

<span data-ttu-id="d8ff5-112">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="d8ff5-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d8ff5-113">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="d8ff5-113">Requirements</span></span>

<span data-ttu-id="d8ff5-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d8ff5-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d8ff5-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d8ff5-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d8ff5-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="d8ff5-116">See also</span></span>

[<span data-ttu-id="d8ff5-117">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="d8ff5-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
