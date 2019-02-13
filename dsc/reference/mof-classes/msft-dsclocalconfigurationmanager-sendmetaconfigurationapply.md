---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: SendMetaConfigurationApply-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: b372a6c0ab9d4561dcf67026275e7d3ca6aa2584
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55679144"
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="b2648-103">SendMetaConfigurationApply-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="b2648-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="b2648-104">Legt die Einstellungen des lokalen Konfigurations-Managers fest, die zur Steuerung des Konfigurations-Agents verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="b2648-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="b2648-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b2648-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="b2648-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="b2648-106">Parameters</span></span>

<span data-ttu-id="b2648-107">*ConfigurationData* \[in\] Die Umgebungsdaten für die Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="b2648-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="b2648-108">*force* \[in\] **true**, um das Beenden der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="b2648-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="b2648-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="b2648-109">Return value</span></span>

<span data-ttu-id="b2648-110">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="b2648-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="b2648-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="b2648-111">Remarks</span></span>

<span data-ttu-id="b2648-112">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="b2648-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="b2648-113">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="b2648-113">Requirements</span></span>

<span data-ttu-id="b2648-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="b2648-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="b2648-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="b2648-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="b2648-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="b2648-116">See also</span></span>

[<span data-ttu-id="b2648-117">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="b2648-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)