---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: ApplyConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 559ff1793a18e28dad2f176bdb20eb53bc08630d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55677624"
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="82931-103">ApplyConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="82931-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="82931-104">Verwendet den Konfigurations-Agent, um die ausstehende Konfiguration anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="82931-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="82931-105">Wenn keine ausstehende Konfiguration vorhanden ist, wendet diese Methode die aktuelle Konfiguration erneut an.</span><span class="sxs-lookup"><span data-stu-id="82931-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="82931-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="82931-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="82931-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="82931-107">Parameters</span></span>

<span data-ttu-id="82931-108">*force* \[in\] Wenn dies **true** ist, wird die aktuelle Konfiguration erneut angewendet, selbst wenn eine Konfiguration aussteht.</span><span class="sxs-lookup"><span data-stu-id="82931-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="82931-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="82931-109">Return value</span></span>

<span data-ttu-id="82931-110">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="82931-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="82931-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="82931-111">Remarks</span></span>

<span data-ttu-id="82931-112">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="82931-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="82931-113">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="82931-113">Requirements</span></span>

<span data-ttu-id="82931-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="82931-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="82931-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="82931-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="82931-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="82931-116">See also</span></span>

[<span data-ttu-id="82931-117">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="82931-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)