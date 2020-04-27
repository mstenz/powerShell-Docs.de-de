---
ms.date: 06/12/2017
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: SendConfigurationApply-Methode
ms.openlocfilehash: 11b9d435bbaac1600d25ff074b6c55b236a8378b
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954887"
---
# <a name="sendconfigurationapply-method"></a><span data-ttu-id="74678-103">SendConfigurationApply-Methode</span><span class="sxs-lookup"><span data-stu-id="74678-103">SendConfigurationApply method</span></span>

<span data-ttu-id="74678-104">Sendet das Konfigurationsdokument an den verwalteten Knoten und verwendet den Konfigurations-Agent zum Anwenden der Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="74678-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="74678-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="74678-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="74678-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="74678-106">Parameters</span></span>

<span data-ttu-id="74678-107">*ConfigurationData* \[in\] Die Umgebungsdaten für die Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="74678-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="74678-108">*force* \[in\] **true**, um das Beenden der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="74678-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="74678-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="74678-109">Return value</span></span>

<span data-ttu-id="74678-110">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="74678-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="74678-111">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="74678-111">Remarks</span></span>

<span data-ttu-id="74678-112">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="74678-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="74678-113">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="74678-113">Requirements</span></span>

<span data-ttu-id="74678-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="74678-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="74678-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="74678-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="74678-116">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="74678-116">See also</span></span>

[<span data-ttu-id="74678-117">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="74678-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
