---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: RollBack-Methode
ms.openlocfilehash: 6452bdffd5160d9956576fb59c98e2f9ff7ddbbb
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727025"
---
# <a name="rollback-method"></a><span data-ttu-id="cca21-103">RollBack-Methode</span><span class="sxs-lookup"><span data-stu-id="cca21-103">RollBack method</span></span>

<span data-ttu-id="cca21-104">Führt einen Rollback der Konfiguration zu einer früheren Version durch.</span><span class="sxs-lookup"><span data-stu-id="cca21-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="cca21-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="cca21-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="cca21-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="cca21-106">Parameters</span></span>

<span data-ttu-id="cca21-107">*configurationNumber* \[in\] Gibt die angeforderte Konfiguration an.</span><span class="sxs-lookup"><span data-stu-id="cca21-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="cca21-108">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="cca21-108">Return value</span></span>

<span data-ttu-id="cca21-109">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="cca21-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="cca21-110">Hinweise</span><span class="sxs-lookup"><span data-stu-id="cca21-110">Remarks</span></span>

<span data-ttu-id="cca21-111">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="cca21-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="cca21-112">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="cca21-112">Requirements</span></span>

<span data-ttu-id="cca21-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="cca21-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="cca21-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="cca21-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="cca21-115">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="cca21-115">See also</span></span>

[<span data-ttu-id="cca21-116">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="cca21-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
