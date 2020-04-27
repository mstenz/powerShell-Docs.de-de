---
ms.date: 06/12/2017
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: SendMetaConfigurationApply-Methode
ms.openlocfilehash: b2e420bafb8ea22aea43800f6e429d3ed785d1e8
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954877"
---
# <a name="sendmetaconfigurationapply-method"></a><span data-ttu-id="861fd-103">SendMetaConfigurationApply-Methode</span><span class="sxs-lookup"><span data-stu-id="861fd-103">SendMetaConfigurationApply method</span></span>

<span data-ttu-id="861fd-104">Legt die Einstellungen des lokalen Konfigurations-Managers fest, die zur Steuerung des Konfigurations-Agents verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="861fd-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="861fd-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="861fd-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="861fd-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="861fd-106">Parameters</span></span>

<span data-ttu-id="861fd-107">*ConfigurationData* \[in\] Die Umgebungsdaten für die Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="861fd-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="861fd-108">*force* \[in\] **true**, um das Beenden der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="861fd-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="861fd-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="861fd-109">Return value</span></span>

<span data-ttu-id="861fd-110">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="861fd-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="861fd-111">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="861fd-111">Remarks</span></span>

<span data-ttu-id="861fd-112">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="861fd-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="861fd-113">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="861fd-113">Requirements</span></span>

<span data-ttu-id="861fd-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="861fd-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="861fd-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="861fd-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="861fd-116">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="861fd-116">See also</span></span>

[<span data-ttu-id="861fd-117">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="861fd-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
