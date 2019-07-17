---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: StopConfiguration-Methode
ms.openlocfilehash: e1de175032a3bddf11af218bc4a15bdbe554a9d5
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67726990"
---
# <a name="stopconfiguration-method"></a><span data-ttu-id="80065-103">StopConfiguration-Methode</span><span class="sxs-lookup"><span data-stu-id="80065-103">StopConfiguration method</span></span>

<span data-ttu-id="80065-104">Beende die Konfigurationsänderung, die gerade ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="80065-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="80065-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="80065-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="80065-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="80065-106">Parameters</span></span>

<span data-ttu-id="80065-107">*force* \[in\] **true**, um das Beenden der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="80065-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="80065-108">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="80065-108">Return value</span></span>

<span data-ttu-id="80065-109">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="80065-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="80065-110">Hinweise</span><span class="sxs-lookup"><span data-stu-id="80065-110">Remarks</span></span>

<span data-ttu-id="80065-111">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="80065-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="80065-112">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="80065-112">Requirements</span></span>

<span data-ttu-id="80065-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="80065-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="80065-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="80065-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="80065-115">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="80065-115">See also</span></span>

[<span data-ttu-id="80065-116">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="80065-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
