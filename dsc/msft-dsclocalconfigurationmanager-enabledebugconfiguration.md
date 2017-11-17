---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: EnableDebugConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 7220c972b3f43b4697cf71df54d2d43881938367
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4de33-103">EnableDebugConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="4de33-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4de33-104">Aktiviert das Debuggen von DSC-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="4de33-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="4de33-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4de33-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="4de33-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="4de33-106">Parameters</span></span>
----------

<span data-ttu-id="4de33-107">*BreakAll* \[in\]</span><span class="sxs-lookup"><span data-stu-id="4de33-107">*BreakAll* \[in\]</span></span>  
<span data-ttu-id="4de33-108">Legt einen Haltepunkt in jeder Zeile im Ressourcenskript fest.</span><span class="sxs-lookup"><span data-stu-id="4de33-108">Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="4de33-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="4de33-109">Return value</span></span>
------------

<span data-ttu-id="4de33-110">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="4de33-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4de33-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="4de33-111">Remarks</span></span>

<span data-ttu-id="4de33-112">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="4de33-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4de33-113">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="4de33-113">Requirements</span></span>
------------
><span data-ttu-id="4de33-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4de33-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="4de33-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4de33-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="4de33-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="4de33-116">See also</span></span>


[<span data-ttu-id="4de33-117">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="4de33-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



