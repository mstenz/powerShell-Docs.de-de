---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: SendConfigurationApply-Methode
ms.openlocfilehash: 11b9d435bbaac1600d25ff074b6c55b236a8378b
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954887"
---
# <a name="sendconfigurationapply-method"></a><span data-ttu-id="ee5ef-103">SendConfigurationApply-Methode</span><span class="sxs-lookup"><span data-stu-id="ee5ef-103">SendConfigurationApply method</span></span>

<span data-ttu-id="ee5ef-104">Sendet das Konfigurationsdokument an den verwalteten Knoten und verwendet den Konfigurations-Agent zum Anwenden der Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="ee5ef-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="ee5ef-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ee5ef-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="ee5ef-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="ee5ef-106">Parameters</span></span>

<span data-ttu-id="ee5ef-107">*ConfigurationData* \[in\] Die Umgebungsdaten für die Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="ee5ef-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="ee5ef-108">*force* \[in\] **true**, um das Beenden der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="ee5ef-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="ee5ef-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="ee5ef-109">Return value</span></span>

<span data-ttu-id="ee5ef-110">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="ee5ef-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ee5ef-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="ee5ef-111">Remarks</span></span>

<span data-ttu-id="ee5ef-112">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="ee5ef-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ee5ef-113">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="ee5ef-113">Requirements</span></span>

<span data-ttu-id="ee5ef-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ee5ef-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="ee5ef-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ee5ef-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="ee5ef-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ee5ef-116">See also</span></span>

[<span data-ttu-id="ee5ef-117">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="ee5ef-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
