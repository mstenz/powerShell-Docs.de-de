---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: GetConfigurationResultOutput-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: f4c2ddaa37cdafeff1a442f3f1fa656788a1c6c8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="5d84a-103">GetConfigurationResultOutput-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="5d84a-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="5d84a-104">Ruft die Konfigurations-Agent-Ausgabe im Zusammenhang mit einem bestimmten Auftrag ab.</span><span class="sxs-lookup"><span data-stu-id="5d84a-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="5d84a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5d84a-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="5d84a-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="5d84a-106">Parameters</span></span>
----------

<span data-ttu-id="5d84a-107">*jobId* \[in\] Die ID des Auftrags, für den Ausgabedaten abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="5d84a-107">*jobId* \[in\] The ID of the job for which to get output data.</span></span>

<span data-ttu-id="5d84a-108">*resumeOutputBookmark* \[in\] Gibt an, dass die Ausgabe eine Fortsetzung eines vorherigen Lesezeichens sein soll.</span><span class="sxs-lookup"><span data-stu-id="5d84a-108">*resumeOutputBookmark* \[in\] Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="5d84a-109">*output* \[out\] Die Ausgabe für den angegebenen Auftrag.</span><span class="sxs-lookup"><span data-stu-id="5d84a-109">*output* \[out\] The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="5d84a-110">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="5d84a-110">Return value</span></span>
------------

<span data-ttu-id="5d84a-111">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="5d84a-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5d84a-112">Hinweise</span><span class="sxs-lookup"><span data-stu-id="5d84a-112">Remarks</span></span>

<span data-ttu-id="5d84a-113">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="5d84a-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5d84a-114">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="5d84a-114">Requirements</span></span>
------------
><span data-ttu-id="5d84a-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5d84a-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="5d84a-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5d84a-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="5d84a-117">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="5d84a-117">See also</span></span>


[<span data-ttu-id="5d84a-118">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="5d84a-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)