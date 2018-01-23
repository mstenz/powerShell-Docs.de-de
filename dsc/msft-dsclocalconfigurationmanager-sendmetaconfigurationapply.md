---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: SendMetaConfigurationApply-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 350555220757b1939b1de34ab423e963635eb53c
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="324ad-103">SendMetaConfigurationApply-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="324ad-103">SendMetaConfigurationApply method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="324ad-104">Legt die Einstellungen des lokalen Konfigurations-Managers fest, die zur Steuerung des Konfigurations-Agents verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="324ad-104">Sets the Local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="324ad-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="324ad-105">Syntax</span></span>
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="324ad-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="324ad-106">Parameters</span></span>
----------

<span data-ttu-id="324ad-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="324ad-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="324ad-108">Die Umgebungsdaten für die Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="324ad-108">The environment data for the configuration.</span></span>

<span data-ttu-id="324ad-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="324ad-109">*force* \[in\]</span></span>  
<span data-ttu-id="324ad-110">**true**, um das Beenden der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="324ad-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="324ad-111">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="324ad-111">Return value</span></span>
------------

<span data-ttu-id="324ad-112">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="324ad-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="324ad-113">Hinweise</span><span class="sxs-lookup"><span data-stu-id="324ad-113">Remarks</span></span>

<span data-ttu-id="324ad-114">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="324ad-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="324ad-115">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="324ad-115">Requirements</span></span>
------------
><span data-ttu-id="324ad-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="324ad-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="324ad-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="324ad-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="324ad-118">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="324ad-118">See also</span></span>


[<span data-ttu-id="324ad-119">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="324ad-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



