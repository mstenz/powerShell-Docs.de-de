---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: ApplyConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 559ff1793a18e28dad2f176bdb20eb53bc08630d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079165"
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="c1ea3-103">ApplyConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="c1ea3-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="c1ea3-104">Verwendet den Konfigurations-Agent, um die ausstehende Konfiguration anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span>

<span data-ttu-id="c1ea3-105">Wenn keine ausstehende Konfiguration vorhanden ist, wendet diese Methode die aktuelle Konfiguration erneut an.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="c1ea3-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="c1ea3-106">Syntax</span></span>

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="c1ea3-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="c1ea3-107">Parameters</span></span>

<span data-ttu-id="c1ea3-108">*force* \[in\] Wenn dies **true** ist, wird die aktuelle Konfiguration erneut angewendet, selbst wenn eine Konfiguration aussteht.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-108">*force* \[in\] If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="c1ea3-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="c1ea3-109">Return value</span></span>

<span data-ttu-id="c1ea3-110">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c1ea3-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="c1ea3-111">Remarks</span></span>

<span data-ttu-id="c1ea3-112">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="c1ea3-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c1ea3-113">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="c1ea3-113">Requirements</span></span>

<span data-ttu-id="c1ea3-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c1ea3-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="c1ea3-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c1ea3-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="c1ea3-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c1ea3-116">See also</span></span>

[<span data-ttu-id="c1ea3-117">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="c1ea3-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)