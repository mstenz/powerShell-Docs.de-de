---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: RollBack-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: a219703389405c0dd457d0b2e0b1c54b9c28f559
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="902af-103">RollBack-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="902af-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="902af-104">Führt einen Rollback der Konfiguration zu einer früheren Version durch.</span><span class="sxs-lookup"><span data-stu-id="902af-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="902af-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="902af-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="902af-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="902af-106">Parameters</span></span>
----------

<span data-ttu-id="902af-107">*configurationNumber* \[in\]</span><span class="sxs-lookup"><span data-stu-id="902af-107">*configurationNumber* \[in\]</span></span>  
<span data-ttu-id="902af-108">Gibt die angeforderte Konfiguration an.</span><span class="sxs-lookup"><span data-stu-id="902af-108">Specifies the requested configuration.</span></span> 

## <a name="return-value"></a><span data-ttu-id="902af-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="902af-109">Return value</span></span>
------------

<span data-ttu-id="902af-110">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="902af-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="902af-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="902af-111">Remarks</span></span>

<span data-ttu-id="902af-112">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="902af-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="902af-113">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="902af-113">Requirements</span></span>
------------
><span data-ttu-id="902af-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="902af-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="902af-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="902af-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="902af-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="902af-116">See also</span></span>


[<span data-ttu-id="902af-117">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="902af-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



