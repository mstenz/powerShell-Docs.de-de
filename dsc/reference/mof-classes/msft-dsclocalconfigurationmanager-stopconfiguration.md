---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: StopConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 1cd887d205967c3d282143df4e6199027639230e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078241"
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="4aedc-103">StopConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="4aedc-103">StopConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="4aedc-104">Beende die Konfigurationsänderung, die gerade ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="4aedc-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="4aedc-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="4aedc-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="4aedc-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="4aedc-106">Parameters</span></span>

<span data-ttu-id="4aedc-107">*force* \[in\] **true**, um das Beenden der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="4aedc-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="4aedc-108">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="4aedc-108">Return value</span></span>

<span data-ttu-id="4aedc-109">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="4aedc-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4aedc-110">Hinweise</span><span class="sxs-lookup"><span data-stu-id="4aedc-110">Remarks</span></span>

<span data-ttu-id="4aedc-111">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="4aedc-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="4aedc-112">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="4aedc-112">Requirements</span></span>

<span data-ttu-id="4aedc-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="4aedc-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="4aedc-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="4aedc-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="4aedc-115">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="4aedc-115">See also</span></span>

[<span data-ttu-id="4aedc-116">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="4aedc-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)