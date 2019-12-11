---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: RollBack-Methode
ms.openlocfilehash: 6452bdffd5160d9956576fb59c98e2f9ff7ddbbb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954937"
---
# <a name="rollback-method"></a><span data-ttu-id="cd5cb-103">RollBack-Methode</span><span class="sxs-lookup"><span data-stu-id="cd5cb-103">RollBack method</span></span>

<span data-ttu-id="cd5cb-104">Führt einen Rollback der Konfiguration zu einer früheren Version durch.</span><span class="sxs-lookup"><span data-stu-id="cd5cb-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="cd5cb-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="cd5cb-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="cd5cb-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="cd5cb-106">Parameters</span></span>

<span data-ttu-id="cd5cb-107">*configurationNumber* \[in\] Gibt die angeforderte Konfiguration an.</span><span class="sxs-lookup"><span data-stu-id="cd5cb-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="cd5cb-108">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="cd5cb-108">Return value</span></span>

<span data-ttu-id="cd5cb-109">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="cd5cb-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="cd5cb-110">Hinweise</span><span class="sxs-lookup"><span data-stu-id="cd5cb-110">Remarks</span></span>

<span data-ttu-id="cd5cb-111">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="cd5cb-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="cd5cb-112">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="cd5cb-112">Requirements</span></span>

<span data-ttu-id="cd5cb-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="cd5cb-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="cd5cb-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="cd5cb-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="cd5cb-115">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="cd5cb-115">See also</span></span>

[<span data-ttu-id="cd5cb-116">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="cd5cb-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
