---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: SendConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 3529bc56ecba19ed0fbbf070a4e86d0692824d39
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078383"
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="ae857-103">SendConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="ae857-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="ae857-104">Sendet das Konfigurationsdokument an den verwalteten Knoten und speichert es als ausstehende Änderung.</span><span class="sxs-lookup"><span data-stu-id="ae857-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

## <a name="syntax"></a><span data-ttu-id="ae857-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ae857-105">Syntax</span></span>

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="ae857-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="ae857-106">Parameters</span></span>

<span data-ttu-id="ae857-107">*ConfigurationData* \[in\] Die Umgebungsdaten für die Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="ae857-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="ae857-108">*force* \[in\] **true**, um das Beenden der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="ae857-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="ae857-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="ae857-109">Return value</span></span>

<span data-ttu-id="ae857-110">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="ae857-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="ae857-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="ae857-111">Remarks</span></span>

<span data-ttu-id="ae857-112">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="ae857-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="ae857-113">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="ae857-113">Requirements</span></span>

<span data-ttu-id="ae857-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="ae857-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="ae857-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="ae857-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="ae857-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ae857-116">See also</span></span>

[<span data-ttu-id="ae857-117">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="ae857-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)