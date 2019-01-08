---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: SendConfigurationApplyAsync-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: b028079cf826719967858f50e357b441ba8f9d79
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047334"
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="8e7e1-103">SendConfigurationApplyAsync-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="8e7e1-103">SendConfigurationApplyAsync method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="8e7e1-104">Sendet das Konfigurationsdokument asynchron an den verwalteten Knoten und verwendet den Konfigurations-Agent, um die Konfiguration anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="8e7e1-104">Sends the configuration document asynchronously to the managed node and uses the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="8e7e1-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8e7e1-105">Syntax</span></span>

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a><span data-ttu-id="8e7e1-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="8e7e1-106">Parameters</span></span>

<span data-ttu-id="8e7e1-107">*ConfigurationData* \[in\] Die Umgebungsdaten für die Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="8e7e1-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="8e7e1-108">*force* \[in\] **true**, um das Beenden der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="8e7e1-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

<span data-ttu-id="8e7e1-109">*jobId* \[in\] Die ID des Auftrags, für den die Konfiguration gesendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="8e7e1-109">*jobId* \[in\] The ID of the job for which to send the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="8e7e1-110">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="8e7e1-110">Return value</span></span>

<span data-ttu-id="8e7e1-111">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="8e7e1-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8e7e1-112">Hinweise</span><span class="sxs-lookup"><span data-stu-id="8e7e1-112">Remarks</span></span>

<span data-ttu-id="8e7e1-113">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="8e7e1-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8e7e1-114">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="8e7e1-114">Requirements</span></span>

<span data-ttu-id="8e7e1-115">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="8e7e1-115">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="8e7e1-116">\*\*Namespace: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="8e7e1-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="8e7e1-117">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="8e7e1-117">See also</span></span>

[<span data-ttu-id="8e7e1-118">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="8e7e1-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)