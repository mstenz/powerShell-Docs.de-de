---
ms.date: 06/12/2017
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: GetConfiguration-Methode
ms.openlocfilehash: eabc536cfe69abe1144ff031a6f64c09a772e638
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71955047"
---
# <a name="getconfiguration-method"></a><span data-ttu-id="31c2d-103">GetConfiguration-Methode</span><span class="sxs-lookup"><span data-stu-id="31c2d-103">GetConfiguration method</span></span>

<span data-ttu-id="31c2d-104">Sendet das Konfigurationsdokument an den verwalteten Knoten und verwendet die **Get**-Methode des Konfigurations-Agents, um die Konfiguration anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="31c2d-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

## <a name="syntax"></a><span data-ttu-id="31c2d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="31c2d-105">Syntax</span></span>

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

## <a name="parameters"></a><span data-ttu-id="31c2d-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="31c2d-106">Parameters</span></span>

<span data-ttu-id="31c2d-107">*configurationData* \[in\] Gibt die zu sendenden Konfigurationsdaten an.</span><span class="sxs-lookup"><span data-stu-id="31c2d-107">*configurationData* \[in\] Specifies the configuration data to send.</span></span>

<span data-ttu-id="31c2d-108">*configurations* \[out\] Enthält bei Rückgabe eine eingebettete Instanz der Konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="31c2d-108">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="31c2d-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="31c2d-109">Return value</span></span>

<span data-ttu-id="31c2d-110">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="31c2d-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="31c2d-111">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="31c2d-111">Remarks</span></span>

<span data-ttu-id="31c2d-112">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="31c2d-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="31c2d-113">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="31c2d-113">Requirements</span></span>

<span data-ttu-id="31c2d-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="31c2d-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="31c2d-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="31c2d-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="31c2d-116">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="31c2d-116">See also</span></span>

[<span data-ttu-id="31c2d-117">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="31c2d-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
