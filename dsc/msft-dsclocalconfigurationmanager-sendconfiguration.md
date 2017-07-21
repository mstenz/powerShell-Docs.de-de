---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: SendConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 8457189538ceb0181a8e65b57a9fc3e911cbcec4
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="sendconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="e6fdc-103">SendConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="e6fdc-103">SendConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="e6fdc-104">Sendet das Konfigurationsdokument an den verwalteten Knoten und speichert es als ausstehende Änderung.</span><span class="sxs-lookup"><span data-stu-id="e6fdc-104">Sends the configuration document to the managed node and saves it as a pending change.</span></span>

<a name="syntax"></a><span data-ttu-id="e6fdc-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e6fdc-105">Syntax</span></span>
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a name="parameters"></a><span data-ttu-id="e6fdc-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="e6fdc-106">Parameters</span></span>
----------

<span data-ttu-id="e6fdc-107">*ConfigurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="e6fdc-107">*ConfigurationData* \[in\]</span></span>  
<span data-ttu-id="e6fdc-108">Die Umgebungsdaten für die Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="e6fdc-108">The environment data for the configuration.</span></span>

<span data-ttu-id="e6fdc-109">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="e6fdc-109">*force* \[in\]</span></span>  
<span data-ttu-id="e6fdc-110">**true**, um das Beenden der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="e6fdc-110">**true** to force the configuration to stop.</span></span>

## <a name="return-value"></a><span data-ttu-id="e6fdc-111">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="e6fdc-111">Return value</span></span>
------------

<span data-ttu-id="e6fdc-112">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="e6fdc-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="e6fdc-113">Hinweise</span><span class="sxs-lookup"><span data-stu-id="e6fdc-113">Remarks</span></span>

<span data-ttu-id="e6fdc-114">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="e6fdc-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="e6fdc-115">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="e6fdc-115">Requirements</span></span>
------------
><span data-ttu-id="e6fdc-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="e6fdc-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="e6fdc-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="e6fdc-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="e6fdc-118">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e6fdc-118">See also</span></span>


[<span data-ttu-id="e6fdc-119">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="e6fdc-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



