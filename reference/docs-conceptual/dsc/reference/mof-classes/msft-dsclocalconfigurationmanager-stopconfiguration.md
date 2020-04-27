---
ms.date: 06/12/2017
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: StopConfiguration-Methode
ms.openlocfilehash: e1de175032a3bddf11af218bc4a15bdbe554a9d5
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953357"
---
# <a name="stopconfiguration-method"></a><span data-ttu-id="ee123-103">StopConfiguration-Methode</span><span class="sxs-lookup"><span data-stu-id="ee123-103">StopConfiguration method</span></span>

<span data-ttu-id="ee123-104">Beende die Konfigurationsänderung, die gerade ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="ee123-104">Stops the configuration change that is in progress.</span></span>

## <a name="syntax"></a><span data-ttu-id="ee123-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ee123-105">Syntax</span></span>

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="ee123-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="ee123-106">Parameters</span></span>

<span data-ttu-id="ee123-107">*force* \[in\] **true**, um das Beenden der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="ee123-107">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="ee123-108">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="ee123-108">Return value</span></span>

<span data-ttu-id="ee123-109">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="ee123-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ee123-110">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="ee123-110">Remarks</span></span>

<span data-ttu-id="ee123-111">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="ee123-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ee123-112">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="ee123-112">Requirements</span></span>

<span data-ttu-id="ee123-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ee123-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="ee123-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ee123-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="ee123-115">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="ee123-115">See also</span></span>

[<span data-ttu-id="ee123-116">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="ee123-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
