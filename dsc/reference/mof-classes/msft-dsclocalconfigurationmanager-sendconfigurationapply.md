---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: SendConfigurationApply-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: da3a08307122ab38ee4a6fd5d4a9b97579a988f7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55678257"
---
# <a name="sendconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="36a6a-103">SendConfigurationApply-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="36a6a-103">SendConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="36a6a-104">Sendet das Konfigurationsdokument an den verwalteten Knoten und verwendet den Konfigurations-Agent zum Anwenden der Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="36a6a-104">Sends the configuration document to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="36a6a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="36a6a-105">Syntax</span></span>

```mof
uint32 SendConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="36a6a-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="36a6a-106">Parameters</span></span>

<span data-ttu-id="36a6a-107">*ConfigurationData* \[in\] Die Umgebungsdaten für die Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="36a6a-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="36a6a-108">*force* \[in\] **true**, um das Beenden der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="36a6a-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="36a6a-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="36a6a-109">Return value</span></span>

<span data-ttu-id="36a6a-110">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="36a6a-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="36a6a-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="36a6a-111">Remarks</span></span>

<span data-ttu-id="36a6a-112">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="36a6a-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="36a6a-113">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="36a6a-113">Requirements</span></span>

<span data-ttu-id="36a6a-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="36a6a-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="36a6a-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="36a6a-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="36a6a-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="36a6a-116">See also</span></span>

[<span data-ttu-id="36a6a-117">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="36a6a-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)