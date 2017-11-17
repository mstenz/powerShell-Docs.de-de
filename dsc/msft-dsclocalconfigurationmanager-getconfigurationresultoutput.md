---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: GetConfigurationResultOutput-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 09862fd3c19e1e517c9bf5df878113ba3f10d8a6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="2c886-103">GetConfigurationResultOutput-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="2c886-103">GetConfigurationResultOutput method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="2c886-104">Ruft die Konfigurations-Agent-Ausgabe im Zusammenhang mit einem bestimmten Auftrag ab.</span><span class="sxs-lookup"><span data-stu-id="2c886-104">Gets the Configuration Agent output associated with a specific job.</span></span>

<a name="syntax"></a><span data-ttu-id="2c886-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="2c886-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a><span data-ttu-id="2c886-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="2c886-106">Parameters</span></span>
----------

<span data-ttu-id="2c886-107">*jobId* \[in\]</span><span class="sxs-lookup"><span data-stu-id="2c886-107">*jobId* \[in\]</span></span>  
<span data-ttu-id="2c886-108">Die ID des Auftrags, für den Ausgabedaten abgerufen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="2c886-108">The ID of the job for which to get output data.</span></span>

<span data-ttu-id="2c886-109">*resumeOutputBookmark* \[in\]</span><span class="sxs-lookup"><span data-stu-id="2c886-109">*resumeOutputBookmark* \[in\]</span></span>  
<span data-ttu-id="2c886-110">Gibt an, dass die Ausgabe eine Fortsetzung eines vorherigen Lesezeichens sein soll.</span><span class="sxs-lookup"><span data-stu-id="2c886-110">Specifies that the output should be a continuation from a previous bookmark.</span></span>

<span data-ttu-id="2c886-111">*output* \[out\]</span><span class="sxs-lookup"><span data-stu-id="2c886-111">*output* \[out\]</span></span>  
<span data-ttu-id="2c886-112">Die Ausgabe für den angegebenen Auftrag.</span><span class="sxs-lookup"><span data-stu-id="2c886-112">The output for the specified job.</span></span>

## <a name="return-value"></a><span data-ttu-id="2c886-113">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="2c886-113">Return value</span></span>
------------

<span data-ttu-id="2c886-114">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="2c886-114">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="2c886-115">Hinweise</span><span class="sxs-lookup"><span data-stu-id="2c886-115">Remarks</span></span>

<span data-ttu-id="2c886-116">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="2c886-116">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="2c886-117">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="2c886-117">Requirements</span></span>
------------
><span data-ttu-id="2c886-118">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="2c886-118">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="2c886-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="2c886-119">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="2c886-120">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="2c886-120">See also</span></span>


[<span data-ttu-id="2c886-121">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="2c886-121">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



