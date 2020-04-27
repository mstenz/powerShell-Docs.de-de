---
ms.date: 06/12/2017
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: SendConfigurationApplyAsync-Methode
ms.openlocfilehash: c0e6dc9418757ee719e848fa8e7006dd73d91ad8
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953377"
---
# <a name="sendconfigurationapplyasync-method"></a><span data-ttu-id="a9889-103">SendConfigurationApplyAsync-Methode</span><span class="sxs-lookup"><span data-stu-id="a9889-103">SendConfigurationApplyAsync method</span></span>

<span data-ttu-id="a9889-104">Sendet das Konfigurationsdokument asynchron an den verwalteten Knoten und verwendet den Konfigurations-Agent, um die Konfiguration anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="a9889-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="a9889-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a9889-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="a9889-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="a9889-106">Parameters</span></span>

<span data-ttu-id="a9889-107">*ConfigurationData* \[in\] Die Umgebungsdaten für die Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="a9889-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="a9889-108">*force* \[in\] **true**, um das Beenden der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="a9889-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="a9889-109">*jobId* \[in\] Die ID des Auftrags, für den die Konfiguration gesendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="a9889-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="a9889-110">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="a9889-110">Return value</span></span>

<span data-ttu-id="a9889-111">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="a9889-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a9889-112">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="a9889-112">Remarks</span></span>

<span data-ttu-id="a9889-113">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="a9889-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="a9889-114">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="a9889-114">Requirements</span></span>

<span data-ttu-id="a9889-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="a9889-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="a9889-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="a9889-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="a9889-117">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="a9889-117">See also</span></span>

[<span data-ttu-id="a9889-118">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="a9889-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
