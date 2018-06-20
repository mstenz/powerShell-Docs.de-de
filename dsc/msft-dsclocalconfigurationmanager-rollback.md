---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: RollBack-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: d2f9b7025d611912e119800408e25fcb66bc0228
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219877"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="62225-103">RollBack-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="62225-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="62225-104">Führt einen Rollback der Konfiguration zu einer früheren Version durch.</span><span class="sxs-lookup"><span data-stu-id="62225-104">Rolls back the configuration to a previous version.</span></span>

<a name="syntax"></a><span data-ttu-id="62225-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="62225-105">Syntax</span></span>
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a><span data-ttu-id="62225-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="62225-106">Parameters</span></span>
----------

<span data-ttu-id="62225-107">*configurationNumber* \[in\] Gibt die angeforderte Konfiguration an.</span><span class="sxs-lookup"><span data-stu-id="62225-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="62225-108">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="62225-108">Return value</span></span>
------------

<span data-ttu-id="62225-109">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="62225-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="62225-110">Hinweise</span><span class="sxs-lookup"><span data-stu-id="62225-110">Remarks</span></span>

<span data-ttu-id="62225-111">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="62225-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="62225-112">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="62225-112">Requirements</span></span>
------------
><span data-ttu-id="62225-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="62225-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="62225-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="62225-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="62225-115">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="62225-115">See also</span></span>


[<span data-ttu-id="62225-116">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="62225-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)