---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: StopConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 66d00cb40750e91e4b369a2e8cebb449697406d9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="78658-103">StopConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="78658-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="78658-104">Beende die Konfigurationsänderung, die gerade ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="78658-104">Stops the configuration change that is in progress.</span></span>

<a name="syntax"></a><span data-ttu-id="78658-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="78658-105">Syntax</span></span>
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="78658-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="78658-106">Parameters</span></span>
----------

<span data-ttu-id="78658-107">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="78658-107">*force* \[in\]</span></span>  
<span data-ttu-id="78658-108">**true**, um das Beenden der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="78658-108">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="78658-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="78658-109">Return value</span></span>
------------

<span data-ttu-id="78658-110">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="78658-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="78658-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="78658-111">Remarks</span></span>

<span data-ttu-id="78658-112">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="78658-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="78658-113">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="78658-113">Requirements</span></span>
------------
><span data-ttu-id="78658-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="78658-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="78658-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="78658-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="78658-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="78658-116">See also</span></span>


[<span data-ttu-id="78658-117">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="78658-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



