---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: SendConfigurationApplyAsync-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: e680bfd1c5b39d364c90cf5ef6b43d0a568af23a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="50c29-103">SendConfigurationApplyAsync-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="50c29-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="50c29-104">Sendet das Konfigurationsdokument asynchron an den verwalteten Knoten und verwendet den Konfigurations-Agent, um die Konfiguration anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="50c29-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="50c29-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="50c29-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

<a name="parameters"></a><span data-ttu-id="50c29-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="50c29-106">Parameters</span></span>
----------

<span data-ttu-id="50c29-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="50c29-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="50c29-108">Die Umgebungsdaten für die Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="50c29-108">The environment data for the configuration.</span></span>

<span data-ttu-id="50c29-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="50c29-109">*force* \[in\]</span></span>  
<span data-ttu-id="50c29-110">**true**, um das Beenden der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="50c29-110">**true** to force the configuration to stop.</span></span>

<span data-ttu-id="50c29-111">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="50c29-111">*jobId* \[in\]</span></span>  
<span data-ttu-id="50c29-112">Die ID des Auftrags, für den die Konfiguration gesendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="50c29-112">The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="50c29-113">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="50c29-113">Return value</span></span>
------------

<span data-ttu-id="50c29-114">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="50c29-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="50c29-115">Hinweise</span><span class="sxs-lookup"><span data-stu-id="50c29-115">Remarks</span></span>

<span data-ttu-id="50c29-116">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="50c29-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="50c29-117">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="50c29-117">Requirements</span></span>
------------
><span data-ttu-id="50c29-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="50c29-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="50c29-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="50c29-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="50c29-120">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="50c29-120">See also</span></span>


[<span data-ttu-id="50c29-121">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="50c29-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



