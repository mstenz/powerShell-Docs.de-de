---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: SendConfigurationApplyAsync-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: e680d510aaac097f4f0de80660274230e028ed45
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e0e56-103">SendConfigurationApplyAsync-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="e0e56-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e0e56-104">Sendet das Konfigurationsdokument asynchron an den verwalteten Knoten und verwendet den Konfigurations-Agent, um die Konfiguration anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="e0e56-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="e0e56-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e0e56-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="e0e56-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="e0e56-106">Parameters</span></span>
----------

<span data-ttu-id="e0e56-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="e0e56-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="e0e56-108">Die Umgebungsdaten für die Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="e0e56-108">The environment data for the configuration.</span></span>

<span data-ttu-id="e0e56-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="e0e56-109">*force* \[in\]</span></span>  
<span data-ttu-id="e0e56-110">**true**, um das Beenden der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="e0e56-110">**true** to force the configuration to stop.</span></span>

<span data-ttu-id="e0e56-111">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="e0e56-111">*jobId* \[in\]</span></span>  
<span data-ttu-id="e0e56-112">Die ID des Auftrags, für den die Konfiguration gesendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="e0e56-112">The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="e0e56-113">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="e0e56-113">Return value</span></span>
------------

<span data-ttu-id="e0e56-114">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="e0e56-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e0e56-115">Hinweise</span><span class="sxs-lookup"><span data-stu-id="e0e56-115">Remarks</span></span>

<span data-ttu-id="e0e56-116">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="e0e56-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e0e56-117">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="e0e56-117">Requirements</span></span>
------------
><span data-ttu-id="e0e56-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e0e56-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="e0e56-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e0e56-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="e0e56-120">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e0e56-120">See also</span></span>


[<span data-ttu-id="e0e56-121">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="e0e56-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



