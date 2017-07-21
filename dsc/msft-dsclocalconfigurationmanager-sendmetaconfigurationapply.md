---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: SendMetaConfigurationApply-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: d8ddc9d99f0d74ad907a6e39ae0e8ac14159be16
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="eecc3-103">SendMetaConfigurationApply-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="eecc3-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="eecc3-104">Legt die Einstellungen des lokalen Konfigurations-Managers fest, die zur Steuerung des Konfigurations-Agents verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="eecc3-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="eecc3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="eecc3-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="eecc3-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="eecc3-106">Parameters</span></span>
----------

<span data-ttu-id="eecc3-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="eecc3-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="eecc3-108">Die Umgebungsdaten für die Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="eecc3-108">The environment data for the configuration.</span></span>

<span data-ttu-id="eecc3-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="eecc3-109">*force* \[in\]</span></span>  
<span data-ttu-id="eecc3-110">**true**, um das Beenden der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="eecc3-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="eecc3-111">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="eecc3-111">Return value</span></span>
------------

<span data-ttu-id="eecc3-112">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="eecc3-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="eecc3-113">Hinweise</span><span class="sxs-lookup"><span data-stu-id="eecc3-113">Remarks</span></span>

<span data-ttu-id="eecc3-114">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="eecc3-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="eecc3-115">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="eecc3-115">Requirements</span></span>
------------
><span data-ttu-id="eecc3-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="eecc3-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="eecc3-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="eecc3-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="eecc3-118">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="eecc3-118">See also</span></span>


[<span data-ttu-id="eecc3-119">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="eecc3-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



