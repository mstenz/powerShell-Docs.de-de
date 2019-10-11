---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: StopConfiguration-Methode
ms.openlocfilehash: e1de175032a3bddf11af218bc4a15bdbe554a9d5
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953357"
---
# <a name="stopconfiguration-method"></a><span data-ttu-id="e7033-103">StopConfiguration-Methode</span><span class="sxs-lookup"><span data-stu-id="e7033-103">StopConfiguration method</span></span>

<span data-ttu-id="e7033-104">Beende die Konfigurationsänderung, die gerade ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="e7033-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="e7033-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e7033-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="e7033-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="e7033-106">Parameters</span></span>

<span data-ttu-id="e7033-107">*force* \[in\] **true**, um das Beenden der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="e7033-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="e7033-108">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="e7033-108">Return value</span></span>

<span data-ttu-id="e7033-109">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="e7033-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e7033-110">Hinweise</span><span class="sxs-lookup"><span data-stu-id="e7033-110">Remarks</span></span>

<span data-ttu-id="e7033-111">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="e7033-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e7033-112">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="e7033-112">Requirements</span></span>

<span data-ttu-id="e7033-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e7033-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e7033-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e7033-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e7033-115">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e7033-115">See also</span></span>

[<span data-ttu-id="e7033-116">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="e7033-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
