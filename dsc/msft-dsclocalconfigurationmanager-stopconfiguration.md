---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: StopConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: f0b550615b20f07f99c8ed7009805c45794bfe22
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="9156c-103">StopConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="9156c-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="9156c-104">Beende die Konfigurationsänderung, die gerade ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="9156c-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="9156c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="9156c-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="9156c-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="9156c-106">Parameters</span></span>
----------

<span data-ttu-id="9156c-107">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="9156c-107">*force* \[in\]</span></span>  
<span data-ttu-id="9156c-108">**true**, um das Beenden der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="9156c-108">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="9156c-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="9156c-109">Return value</span></span>
------------

<span data-ttu-id="9156c-110">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="9156c-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="9156c-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="9156c-111">Remarks</span></span>

<span data-ttu-id="9156c-112">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="9156c-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="9156c-113">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="9156c-113">Requirements</span></span>
------------
><span data-ttu-id="9156c-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="9156c-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="9156c-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="9156c-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="9156c-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="9156c-116">See also</span></span>


[<span data-ttu-id="9156c-117">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="9156c-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



