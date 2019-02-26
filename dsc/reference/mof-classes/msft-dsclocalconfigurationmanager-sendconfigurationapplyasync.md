---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: SendConfigurationApplyAsync-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: b028079cf826719967858f50e357b441ba8f9d79
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679471"
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7e3a4-103">SendConfigurationApplyAsync-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="7e3a4-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7e3a4-104">Sendet das Konfigurationsdokument asynchron an den verwalteten Knoten und verwendet den Konfigurations-Agent, um die Konfiguration anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="7e3a4-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="7e3a4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7e3a4-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="7e3a4-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="7e3a4-106">Parameters</span></span>

<span data-ttu-id="7e3a4-107">*ConfigurationData* \[in\] Die Umgebungsdaten für die Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="7e3a4-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="7e3a4-108">*force* \[in\] **true**, um das Beenden der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="7e3a4-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="7e3a4-109">*jobId* \[in\] Die ID des Auftrags, für den die Konfiguration gesendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="7e3a4-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="7e3a4-110">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="7e3a4-110">Return value</span></span>

<span data-ttu-id="7e3a4-111">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="7e3a4-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7e3a4-112">Hinweise</span><span class="sxs-lookup"><span data-stu-id="7e3a4-112">Remarks</span></span>

<span data-ttu-id="7e3a4-113">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="7e3a4-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7e3a4-114">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="7e3a4-114">Requirements</span></span>

<span data-ttu-id="7e3a4-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7e3a4-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="7e3a4-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7e3a4-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="7e3a4-117">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="7e3a4-117">See also</span></span>

[<span data-ttu-id="7e3a4-118">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="7e3a4-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)