---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: RollBack-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 4956900ecd2c9cb7f2e2b5bcab94616f9f5d5565
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893017"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="78afb-103">RollBack-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="78afb-103">RollBack method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="78afb-104">Führt einen Rollback der Konfiguration zu einer früheren Version durch.</span><span class="sxs-lookup"><span data-stu-id="78afb-104">Rolls back the configuration to a previous version.</span></span>

## <a name="syntax"></a><span data-ttu-id="78afb-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="78afb-105">Syntax</span></span>

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a><span data-ttu-id="78afb-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="78afb-106">Parameters</span></span>

<span data-ttu-id="78afb-107">*configurationNumber* \[in\] Gibt die angeforderte Konfiguration an.</span><span class="sxs-lookup"><span data-stu-id="78afb-107">*configurationNumber* \[in\] Specifies the requested configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="78afb-108">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="78afb-108">Return value</span></span>

<span data-ttu-id="78afb-109">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="78afb-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="78afb-110">Hinweise</span><span class="sxs-lookup"><span data-stu-id="78afb-110">Remarks</span></span>

<span data-ttu-id="78afb-111">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="78afb-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="78afb-112">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="78afb-112">Requirements</span></span>

<span data-ttu-id="78afb-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="78afb-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="78afb-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="78afb-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="78afb-115">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="78afb-115">See also</span></span>

[<span data-ttu-id="78afb-116">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="78afb-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)