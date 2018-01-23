---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: EnableDebugConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: fa34a583af7c3fd46d99307d582973410e4c0e31
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="08424-103">EnableDebugConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="08424-103">EnableDebugConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="08424-104">Aktiviert das Debuggen von DSC-Ressourcen.</span><span class="sxs-lookup"><span data-stu-id="08424-104">Enables DSC resource debugging.</span></span>

<a name="syntax"></a><span data-ttu-id="08424-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="08424-105">Syntax</span></span>
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a><span data-ttu-id="08424-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="08424-106">Parameters</span></span>
----------

<span data-ttu-id="08424-107">*BreakAll* \[in\]</span><span class="sxs-lookup"><span data-stu-id="08424-107">*BreakAll* \[in\]</span></span>  
<span data-ttu-id="08424-108">Legt einen Haltepunkt in jeder Zeile im Ressourcenskript fest.</span><span class="sxs-lookup"><span data-stu-id="08424-108">Sets a breakpoint at every line in the resource script.</span></span>

## <a name="return-value"></a><span data-ttu-id="08424-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="08424-109">Return value</span></span>
------------

<span data-ttu-id="08424-110">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="08424-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="08424-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="08424-111">Remarks</span></span>

<span data-ttu-id="08424-112">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="08424-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="08424-113">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="08424-113">Requirements</span></span>
------------
><span data-ttu-id="08424-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="08424-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="08424-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="08424-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="08424-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="08424-116">See also</span></span>


[<span data-ttu-id="08424-117">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="08424-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



