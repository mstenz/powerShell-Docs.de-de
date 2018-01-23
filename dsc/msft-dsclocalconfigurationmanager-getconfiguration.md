---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: GetConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 60f4b49575dbb28ce74af0500e6982ec5d2e7a66
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="20386-103">GetConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="20386-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="20386-104">Sendet das Konfigurationsdokument an den verwalteten Knoten und verwendet die **Get**-Methode des Konfigurations-Agents, um die Konfiguration anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="20386-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="20386-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="20386-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="20386-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="20386-106">Parameters</span></span>
----------

<span data-ttu-id="20386-107">*configurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="20386-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="20386-108">Gibt die zu sendenden Konfigurationsdaten an.</span><span class="sxs-lookup"><span data-stu-id="20386-108">Specifies the configuration data to send.</span></span>

<span data-ttu-id="20386-109">*configurations* \[out\]</span><span class="sxs-lookup"><span data-stu-id="20386-109">*configurations* \[out\]</span></span>  
<span data-ttu-id="20386-110">Enthält bei Rückgabe eine eingebettete Instanz der Konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="20386-110">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="20386-111">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="20386-111">Return value</span></span>
------------

<span data-ttu-id="20386-112">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="20386-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="20386-113">Hinweise</span><span class="sxs-lookup"><span data-stu-id="20386-113">Remarks</span></span>

<span data-ttu-id="20386-114">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="20386-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="20386-115">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="20386-115">Requirements</span></span>
------------
><span data-ttu-id="20386-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="20386-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="20386-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="20386-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="20386-118">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="20386-118">See also</span></span>


[<span data-ttu-id="20386-119">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="20386-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



