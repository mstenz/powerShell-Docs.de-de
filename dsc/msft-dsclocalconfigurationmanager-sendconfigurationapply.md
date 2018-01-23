---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: SendConfigurationApply-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 20f732d35860cccde4e507dc6916e27d0cf8c5f6
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b6501-103">SendConfigurationApply-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="b6501-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b6501-104">Sendet das Konfigurationsdokument an den verwalteten Knoten und verwendet den Konfigurations-Agent zum Anwenden der Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="b6501-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="b6501-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b6501-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="b6501-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="b6501-106">Parameters</span></span>
----------

<span data-ttu-id="b6501-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="b6501-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="b6501-108">Die Umgebungsdaten für die Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="b6501-108">The environment data for the configuration.</span></span>

<span data-ttu-id="b6501-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="b6501-109">*force* \[in\]</span></span>  
<span data-ttu-id="b6501-110">**true**, um das Beenden der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="b6501-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="b6501-111">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="b6501-111">Return value</span></span>
------------

<span data-ttu-id="b6501-112">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="b6501-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b6501-113">Hinweise</span><span class="sxs-lookup"><span data-stu-id="b6501-113">Remarks</span></span>

<span data-ttu-id="b6501-114">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="b6501-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b6501-115">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="b6501-115">Requirements</span></span>
------------
><span data-ttu-id="b6501-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b6501-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="b6501-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b6501-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="b6501-118">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b6501-118">See also</span></span>


[<span data-ttu-id="b6501-119">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="b6501-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



