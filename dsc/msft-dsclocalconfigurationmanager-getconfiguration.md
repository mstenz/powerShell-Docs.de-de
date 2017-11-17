---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: GetConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 96676a76a0302543e5e4a214c82ed952d7f52a71
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="getconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="639e3-103">GetConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="639e3-103">GetConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="639e3-104">Sendet das Konfigurationsdokument an den verwalteten Knoten und verwendet die **Get**-Methode des Konfigurations-Agents, um die Konfiguration anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="639e3-104">Sends the configuration document to the managed node and uses the **Get** method of the Configuration Agent to apply the configuration.</span></span>

<a name="syntax"></a><span data-ttu-id="639e3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="639e3-105">Syntax</span></span>
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

<a name="parameters"></a><span data-ttu-id="639e3-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="639e3-106">Parameters</span></span>
----------

<span data-ttu-id="639e3-107">*configurationData* \[in\]</span><span class="sxs-lookup"><span data-stu-id="639e3-107">*configurationData* \[in\]</span></span>  
<span data-ttu-id="639e3-108">Gibt die zu sendenden Konfigurationsdaten an.</span><span class="sxs-lookup"><span data-stu-id="639e3-108">Specifies the configuration data to send.</span></span>

<span data-ttu-id="639e3-109">*configurations* \[out\]</span><span class="sxs-lookup"><span data-stu-id="639e3-109">*configurations* \[out\]</span></span>  
<span data-ttu-id="639e3-110">Enthält bei Rückgabe eine eingebettete Instanz der Konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="639e3-110">On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="639e3-111">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="639e3-111">Return value</span></span>
------------

<span data-ttu-id="639e3-112">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="639e3-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="639e3-113">Hinweise</span><span class="sxs-lookup"><span data-stu-id="639e3-113">Remarks</span></span>

<span data-ttu-id="639e3-114">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="639e3-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="639e3-115">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="639e3-115">Requirements</span></span>
------------
><span data-ttu-id="639e3-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="639e3-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="639e3-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="639e3-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="639e3-118">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="639e3-118">See also</span></span>


[<span data-ttu-id="639e3-119">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="639e3-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
 

 



