---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: SendConfigurationApply-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 8edf8c55089e767394ba21b42fe74072777a45c9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7609b-103">SendConfigurationApply-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="7609b-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7609b-104">Sendet das Konfigurationsdokument an den verwalteten Knoten und verwendet den Konfigurations-Agent zum Anwenden der Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="7609b-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="7609b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7609b-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="7609b-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="7609b-106">Parameters</span></span>
----------

<span data-ttu-id="7609b-107">*ConfigurationData* \[in\] Die Umgebungsdaten für die Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="7609b-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="7609b-108">*force* \[in\] **true**, um das Beenden der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="7609b-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="7609b-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="7609b-109">Return value</span></span>
------------

<span data-ttu-id="7609b-110">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="7609b-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7609b-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="7609b-111">Remarks</span></span>

<span data-ttu-id="7609b-112">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="7609b-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7609b-113">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="7609b-113">Requirements</span></span>
------------
><span data-ttu-id="7609b-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7609b-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="7609b-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7609b-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="7609b-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="7609b-116">See also</span></span>


[<span data-ttu-id="7609b-117">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="7609b-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)