---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: GetConfigurationResultOutput-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: f6106bb28dc20004b5bbb6df2d8e719cf0c453f0
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="6ac6d-103">GetConfigurationResultOutput-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="6ac6d-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="6ac6d-104">Ruft die Konfigurations-Agent-Ausgabe im Zusammenhang mit einem bestimmten Auftrag ab.</span><span class="sxs-lookup"><span data-stu-id="6ac6d-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="6ac6d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6ac6d-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="6ac6d-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="6ac6d-106">Parameters</span></span>
----------

<span data-ttu-id="6ac6d-107">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="6ac6d-107">*jobId* \[in\]</span></span>  
<span data-ttu-id="6ac6d-108">Die ID des Auftrags, für den Ausgabedaten abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="6ac6d-108">The ID of the job for which to get output data.</span></span>

<span data-ttu-id="6ac6d-109">*resumeOutputBookmark* \[in\]</span><span class="sxs-lookup"><span data-stu-id="6ac6d-109">*resumeOutputBookmark* \[in\]</span></span>  
<span data-ttu-id="6ac6d-110">Gibt an, dass die Ausgabe eine Fortsetzung eines vorherigen Lesezeichens sein soll.</span><span class="sxs-lookup"><span data-stu-id="6ac6d-110">Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="6ac6d-111">*output* \[out\]</span><span class="sxs-lookup"><span data-stu-id="6ac6d-111">*output* \[out\]</span></span>  
<span data-ttu-id="6ac6d-112">Die Ausgabe für den angegebenen Auftrag.</span><span class="sxs-lookup"><span data-stu-id="6ac6d-112">The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="6ac6d-113">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="6ac6d-113">Return value</span></span>
------------

<span data-ttu-id="6ac6d-114">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="6ac6d-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="6ac6d-115">Hinweise</span><span class="sxs-lookup"><span data-stu-id="6ac6d-115">Remarks</span></span>

<span data-ttu-id="6ac6d-116">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="6ac6d-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="6ac6d-117">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="6ac6d-117">Requirements</span></span>
------------
><span data-ttu-id="6ac6d-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="6ac6d-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="6ac6d-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="6ac6d-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="6ac6d-120">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="6ac6d-120">See also</span></span>


[<span data-ttu-id="6ac6d-121">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="6ac6d-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



