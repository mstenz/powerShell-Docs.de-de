---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: StopConfiguration-Methode
ms.openlocfilehash: e1de175032a3bddf11af218bc4a15bdbe554a9d5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953357"
---
# <a name="stopconfiguration-method"></a><span data-ttu-id="5213c-103">StopConfiguration-Methode</span><span class="sxs-lookup"><span data-stu-id="5213c-103">StopConfiguration method</span></span>

<span data-ttu-id="5213c-104">Beende die Konfigurationsänderung, die gerade ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="5213c-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="5213c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5213c-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="5213c-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="5213c-106">Parameters</span></span>

<span data-ttu-id="5213c-107">*force* \[in\] **true**, um das Beenden der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="5213c-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="5213c-108">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="5213c-108">Return value</span></span>

<span data-ttu-id="5213c-109">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="5213c-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5213c-110">Hinweise</span><span class="sxs-lookup"><span data-stu-id="5213c-110">Remarks</span></span>

<span data-ttu-id="5213c-111">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="5213c-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5213c-112">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="5213c-112">Requirements</span></span>

<span data-ttu-id="5213c-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5213c-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="5213c-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5213c-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="5213c-115">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="5213c-115">See also</span></span>

[<span data-ttu-id="5213c-116">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="5213c-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
