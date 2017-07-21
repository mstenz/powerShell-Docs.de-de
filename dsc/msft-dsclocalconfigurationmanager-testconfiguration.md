---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: TestConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 8e9986837aaf41b1396a2399c58675bc51b0b708
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="5b894-103">TestConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="5b894-103">TestConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="5b894-104">Sendet das Konfigurationsdokument an den verwalteten Knoten und überprüft die aktuelle Konfiguration anhand dieses Dokuments.</span><span class="sxs-lookup"><span data-stu-id="5b894-104">Sends the configuration document to the managed node and verifies the current configuration against the document.</span></span>

<a name="syntax"></a><span data-ttu-id="5b894-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5b894-105">Syntax</span></span>
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a><span data-ttu-id="5b894-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="5b894-106">Parameters</span></span>
----------

<span data-ttu-id="5b894-107">*configurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="5b894-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="5b894-108">Umgebungsdaten für die Konfiguration.</span><span class="sxs-lookup"><span data-stu-id="5b894-108">Environment data for the confuguration.</span></span>

<span data-ttu-id="5b894-109">*InDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="5b894-109">*InDesiredState* \[out\]</span></span>  
<span data-ttu-id="5b894-110">Gibt bei der Rückgabe an, ob sich der verwaltete Knoten im vom Konfigurationsdokument angegebenen Zustand befindet.</span><span class="sxs-lookup"><span data-stu-id="5b894-110">On return, specifies whether the managed node is in the state specified by the configuration document.</span></span>

<span data-ttu-id="5b894-111">*ResourcesInDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="5b894-111">*ResourcesInDesiredState* \[out\]</span></span>  
<span data-ttu-id="5b894-112">Enthält bei der Rückgabe eine eingebettete Instanz der **MSFT_ResourceInDesiredState**-Klasse, die Ressourcen angibt, die sich im gewünschten Zustand befinden.</span><span class="sxs-lookup"><span data-stu-id="5b894-112">On return, contains an embedded instance of the **MSFT_ResourceInDesiredState** class that specifies resources that are in the desired state.</span></span>

<span data-ttu-id="5b894-113">*ResourcesNotInDesiredState* \[out\]</span><span class="sxs-lookup"><span data-stu-id="5b894-113">*ResourcesNotInDesiredState* \[out\]</span></span>  
<span data-ttu-id="5b894-114">Enthält bei der Rückgabe eine eingebettete Instanz der **MSFT_ResourceNotInDesiredState**-Klasse, die Ressourcen angibt, die sich nicht im gewünschten Zustand befinden.</span><span class="sxs-lookup"><span data-stu-id="5b894-114">On return, contains an embedded instance of the **MSFT_ResourceNotInDesiredState** class that specifies resources that are not in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="5b894-115">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="5b894-115">Return value</span></span>
------------

<span data-ttu-id="5b894-116">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="5b894-116">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5b894-117">Hinweise</span><span class="sxs-lookup"><span data-stu-id="5b894-117">Remarks</span></span>

<span data-ttu-id="5b894-118">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="5b894-118">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5b894-119">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="5b894-119">Requirements</span></span>
------------
><span data-ttu-id="5b894-120">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5b894-120">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="5b894-121">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5b894-121">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="5b894-122">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="5b894-122">See also</span></span>


[<span data-ttu-id="5b894-123">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="5b894-123">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



