---
ms.date: 06/12/2017
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: SendConfiguration-Methode
ms.openlocfilehash: 4feba090bc58844659c2329a304dd9805255564f
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953387"
---
# <a name="sendconfiguration-method"></a><span data-ttu-id="64f0f-103">SendConfiguration-Methode</span><span class="sxs-lookup"><span data-stu-id="64f0f-103">SendConfiguration method</span></span>

<span data-ttu-id="64f0f-104">Sendet das Konfigurationsdokument an den verwalteten Knoten und speichert es als ausstehende Änderung.</span><span class="sxs-lookup"><span data-stu-id="64f0f-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="64f0f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="64f0f-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="64f0f-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="64f0f-106">Parameters</span></span>

<span data-ttu-id="64f0f-107">*ConfigurationData* \[in\] Die Umgebungsdaten für die Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="64f0f-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="64f0f-108">*force* \[in\] **true**, um das Beenden der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="64f0f-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="64f0f-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="64f0f-109">Return value</span></span>

<span data-ttu-id="64f0f-110">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="64f0f-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="64f0f-111">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="64f0f-111">Remarks</span></span>

<span data-ttu-id="64f0f-112">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="64f0f-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="64f0f-113">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="64f0f-113">Requirements</span></span>

<span data-ttu-id="64f0f-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="64f0f-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="64f0f-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="64f0f-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="64f0f-116">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="64f0f-116">See also</span></span>

[<span data-ttu-id="64f0f-117">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="64f0f-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
