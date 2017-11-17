---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: RollBack-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: b8597e3eb7872d9894863fb02d927c9f475da44c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="1dae9-103">RollBack-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="1dae9-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="1dae9-104">Führt einen Rollback der Konfiguration zu einer früheren Version durch.</span><span class="sxs-lookup"><span data-stu-id="1dae9-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="1dae9-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1dae9-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="1dae9-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="1dae9-106">Parameters</span></span>
----------

<span data-ttu-id="1dae9-107">*configurationNumber* \[in\]</span><span class="sxs-lookup"><span data-stu-id="1dae9-107">*configurationNumber* \[in\]</span></span>  
<span data-ttu-id="1dae9-108">Gibt die angeforderte Konfiguration an.</span><span class="sxs-lookup"><span data-stu-id="1dae9-108">Specifies the requested configuration.</span></span> 

## <a name="return-value"></a><span data-ttu-id="1dae9-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="1dae9-109">Return value</span></span>
------------

<span data-ttu-id="1dae9-110">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="1dae9-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="1dae9-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="1dae9-111">Remarks</span></span>

<span data-ttu-id="1dae9-112">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="1dae9-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1dae9-113">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="1dae9-113">Requirements</span></span>
------------
><span data-ttu-id="1dae9-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="1dae9-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="1dae9-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="1dae9-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="1dae9-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="1dae9-116">See also</span></span>


[<span data-ttu-id="1dae9-117">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="1dae9-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



