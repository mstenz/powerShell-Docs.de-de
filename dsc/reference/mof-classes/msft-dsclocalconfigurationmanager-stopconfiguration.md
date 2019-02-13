---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: StopConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 1cd887d205967c3d282143df4e6199027639230e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679009"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e4953-103">StopConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="e4953-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e4953-104">Beende die Konfigurationsänderung, die gerade ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="e4953-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="e4953-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e4953-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="e4953-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="e4953-106">Parameters</span></span>

<span data-ttu-id="e4953-107">*force* \[in\] **true**, um das Beenden der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="e4953-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="e4953-108">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="e4953-108">Return value</span></span>

<span data-ttu-id="e4953-109">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="e4953-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e4953-110">Hinweise</span><span class="sxs-lookup"><span data-stu-id="e4953-110">Remarks</span></span>

<span data-ttu-id="e4953-111">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="e4953-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e4953-112">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="e4953-112">Requirements</span></span>

<span data-ttu-id="e4953-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e4953-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="e4953-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e4953-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="e4953-115">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e4953-115">See also</span></span>

[<span data-ttu-id="e4953-116">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="e4953-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)