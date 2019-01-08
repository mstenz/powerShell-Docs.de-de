---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: SendMetaConfigurationApply-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: b372a6c0ab9d4561dcf67026275e7d3ca6aa2584
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047854"
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="3e901-103">SendMetaConfigurationApply-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="3e901-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="3e901-104">Legt die Einstellungen des lokalen Konfigurations-Managers fest, die zur Steuerung des Konfigurations-Agents verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="3e901-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="3e901-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3e901-105">Syntax</span></span>

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="3e901-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="3e901-106">Parameters</span></span>

<span data-ttu-id="3e901-107">*ConfigurationData* \[in\] Die Umgebungsdaten für die Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="3e901-107">*ConfigurationData* \[in\] The environment data for the configuration.</span></span>

<span data-ttu-id="3e901-108">*force* \[in\] **true**, um das Beenden der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="3e901-108">*force* \[in\] **true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="3e901-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="3e901-109">Return value</span></span>

<span data-ttu-id="3e901-110">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="3e901-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="3e901-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="3e901-111">Remarks</span></span>

<span data-ttu-id="3e901-112">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="3e901-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="3e901-113">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="3e901-113">Requirements</span></span>

<span data-ttu-id="3e901-114">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="3e901-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="3e901-115">\*\*Namespace: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="3e901-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="3e901-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="3e901-116">See also</span></span>

[<span data-ttu-id="3e901-117">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="3e901-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)