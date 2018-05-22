---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: SendConfigurationApply-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: c578f4f52d3ea70e7bcf683ac204d6e484d4630d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="94d36-103">SendConfigurationApply-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="94d36-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="94d36-104">Sendet das Konfigurationsdokument an den verwalteten Knoten und verwendet den Konfigurations-Agent zum Anwenden der Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="94d36-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="94d36-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="94d36-105">Syntax</span></span>
------

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="94d36-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="94d36-106">Parameters</span></span>
----------

<span data-ttu-id="94d36-107">*ConfigurationData* \[in\] Die Umgebungsdaten für die Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="94d36-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="94d36-108">*force* \[in\] **true**, um das Beenden der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="94d36-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="94d36-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="94d36-109">Return value</span></span>
------------

<span data-ttu-id="94d36-110">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="94d36-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="94d36-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="94d36-111">Remarks</span></span>

<span data-ttu-id="94d36-112">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="94d36-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="94d36-113">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="94d36-113">Requirements</span></span>
------------
><span data-ttu-id="94d36-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="94d36-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="94d36-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="94d36-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="94d36-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="94d36-116">See also</span></span>


[<span data-ttu-id="94d36-117">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="94d36-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)