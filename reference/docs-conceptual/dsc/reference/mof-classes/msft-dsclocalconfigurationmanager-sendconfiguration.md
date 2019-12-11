---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: SendConfiguration-Methode
ms.openlocfilehash: 4feba090bc58844659c2329a304dd9805255564f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953387"
---
# <a name="sendconfiguration-method"></a><span data-ttu-id="fbef7-103">SendConfiguration-Methode</span><span class="sxs-lookup"><span data-stu-id="fbef7-103">SendConfiguration method</span></span>

<span data-ttu-id="fbef7-104">Sendet das Konfigurationsdokument an den verwalteten Knoten und speichert es als ausstehende Änderung.</span><span class="sxs-lookup"><span data-stu-id="fbef7-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="fbef7-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="fbef7-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="fbef7-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="fbef7-106">Parameters</span></span>

<span data-ttu-id="fbef7-107">*ConfigurationData* \[in\] Die Umgebungsdaten für die Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="fbef7-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="fbef7-108">*force* \[in\] **true**, um das Beenden der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="fbef7-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="fbef7-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="fbef7-109">Return value</span></span>

<span data-ttu-id="fbef7-110">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="fbef7-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="fbef7-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="fbef7-111">Remarks</span></span>

<span data-ttu-id="fbef7-112">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="fbef7-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="fbef7-113">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="fbef7-113">Requirements</span></span>

<span data-ttu-id="fbef7-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="fbef7-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="fbef7-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="fbef7-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="fbef7-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="fbef7-116">See also</span></span>

[<span data-ttu-id="fbef7-117">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="fbef7-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
