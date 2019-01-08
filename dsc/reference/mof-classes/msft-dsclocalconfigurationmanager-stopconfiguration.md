---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: StopConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 1cd887d205967c3d282143df4e6199027639230e
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047251"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="6b475-103">StopConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="6b475-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="6b475-104">Beende die Konfigurationsänderung, die gerade ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="6b475-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="6b475-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6b475-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="6b475-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="6b475-106">Parameters</span></span>

<span data-ttu-id="6b475-107">*force* \[in\] **true**, um das Beenden der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="6b475-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="6b475-108">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="6b475-108">Return value</span></span>

<span data-ttu-id="6b475-109">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="6b475-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="6b475-110">Hinweise</span><span class="sxs-lookup"><span data-stu-id="6b475-110">Remarks</span></span>

<span data-ttu-id="6b475-111">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="6b475-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="6b475-112">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="6b475-112">Requirements</span></span>

<span data-ttu-id="6b475-113">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="6b475-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="6b475-114">\*\*Namespace: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="6b475-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="6b475-115">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="6b475-115">See also</span></span>

[<span data-ttu-id="6b475-116">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="6b475-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)