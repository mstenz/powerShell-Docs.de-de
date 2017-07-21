---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: ApplyConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: febaf972a2a452eb9aaf3ec7fbc5e41f3f463a58
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="f6cad-103">ApplyConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="f6cad-103">ApplyConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="f6cad-104">Verwendet den Konfigurations-Agent, um die ausstehende Konfiguration anzuwenden.</span><span class="sxs-lookup"><span data-stu-id="f6cad-104">Uses the Configuration Agent to apply the configuration that is pending.</span></span> 

<span data-ttu-id="f6cad-105">Wenn keine ausstehende Konfiguration vorhanden ist, wendet diese Methode die aktuelle Konfiguration erneut an.</span><span class="sxs-lookup"><span data-stu-id="f6cad-105">If there is no configuration pending, this method reapplies the current configuration.</span></span>


## <a name="syntax"></a><span data-ttu-id="f6cad-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f6cad-106">Syntax</span></span>
------

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a><span data-ttu-id="f6cad-107">Parameter</span><span class="sxs-lookup"><span data-stu-id="f6cad-107">Parameters</span></span>
----------

<span data-ttu-id="f6cad-108">*force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="f6cad-108">*force* \[in\]</span></span>  
<span data-ttu-id="f6cad-109">Wenn dies **true** ist, wird die aktuelle Konfiguration erneut angewendet, auch wenn eine Konfiguration aussteht.</span><span class="sxs-lookup"><span data-stu-id="f6cad-109">If this is **true**, the current configuration is reapplied, even if there is a configuration pending.</span></span>

## <a name="return-value"></a><span data-ttu-id="f6cad-110">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="f6cad-110">Return value</span></span>
------------

<span data-ttu-id="f6cad-111">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="f6cad-111">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f6cad-112">Hinweise</span><span class="sxs-lookup"><span data-stu-id="f6cad-112">Remarks</span></span>

<span data-ttu-id="f6cad-113">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="f6cad-113">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f6cad-114">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="f6cad-114">Requirements</span></span>
------------
><span data-ttu-id="f6cad-115">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f6cad-115">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="f6cad-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f6cad-116">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="f6cad-117">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f6cad-117">See also</span></span>


[<span data-ttu-id="f6cad-118">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="f6cad-118">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)

 

 



