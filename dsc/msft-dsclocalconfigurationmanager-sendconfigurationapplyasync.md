---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: SendConfigurationApplyAsync-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 7ff821a277a548869862741551ee9897e417ea45
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="eb390-103">SendConfigurationApplyAsync-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="eb390-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="eb390-104">Sendet das Konfigurationsdokument asynchron an den verwalteten Knoten und verwendet den Konfigurations-Agent, um die Konfiguration anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="eb390-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="eb390-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="eb390-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="eb390-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="eb390-106">Parameters</span></span>
----------

<span data-ttu-id="eb390-107">*ConfigurationData* \[in\] Die Umgebungsdaten für die Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="eb390-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="eb390-108">*force* \[in\] **true**, um das Beenden der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="eb390-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="eb390-109">*jobId* \[in\] Die ID des Auftrags, für den die Konfiguration gesendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="eb390-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="eb390-110">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="eb390-110">Return value</span></span>
------------

<span data-ttu-id="eb390-111">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="eb390-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="eb390-112">Hinweise</span><span class="sxs-lookup"><span data-stu-id="eb390-112">Remarks</span></span>

<span data-ttu-id="eb390-113">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="eb390-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="eb390-114">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="eb390-114">Requirements</span></span>
------------
><span data-ttu-id="eb390-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="eb390-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="eb390-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="eb390-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="eb390-117">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="eb390-117">See also</span></span>


[<span data-ttu-id="eb390-118">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="eb390-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)