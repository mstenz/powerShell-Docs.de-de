---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: RemoveConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: e0ae8a50212b70841d210d7b2d666a2855218d1a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="33ac5-103">RemoveConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="33ac5-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="33ac5-104">Entfernt die Konfigurationsdateien.</span><span class="sxs-lookup"><span data-stu-id="33ac5-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="33ac5-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="33ac5-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="33ac5-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="33ac5-106">Parameters</span></span>
----------

<span data-ttu-id="33ac5-107">*Stage* \[in\] Gibt an, welches Konfigurationsdokument entfernt werden soll.</span><span class="sxs-lookup"><span data-stu-id="33ac5-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="33ac5-108">Die folgenden Werte sind gültig:</span><span class="sxs-lookup"><span data-stu-id="33ac5-108">The following values are valid:</span></span>

|<span data-ttu-id="33ac5-109">Wert</span><span class="sxs-lookup"><span data-stu-id="33ac5-109">Value</span></span> |<span data-ttu-id="33ac5-110">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="33ac5-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="33ac5-111">**1**</span><span class="sxs-lookup"><span data-stu-id="33ac5-111">**1**</span></span> | <span data-ttu-id="33ac5-112">Das **aktuelle** (Current) Konfigurationsdokument (current.mof).</span><span class="sxs-lookup"><span data-stu-id="33ac5-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="33ac5-113">**2**</span><span class="sxs-lookup"><span data-stu-id="33ac5-113">**2**</span></span> | <span data-ttu-id="33ac5-114">Das **ausstehende** (Pending) Konfigurationsdokument (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="33ac5-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="33ac5-115">**4**</span><span class="sxs-lookup"><span data-stu-id="33ac5-115">**4**</span></span> | <span data-ttu-id="33ac5-116">Das **vorherige** (Previous) Konfigurationsdokument (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="33ac5-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="33ac5-117">*Force* \[in\] **true**, um das Entfernen der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="33ac5-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="33ac5-118">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="33ac5-118">Return value</span></span>
------------

<span data-ttu-id="33ac5-119">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="33ac5-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="33ac5-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="33ac5-120">Remarks</span></span>

<span data-ttu-id="33ac5-121">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="33ac5-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="33ac5-122">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="33ac5-122">Requirements</span></span>
------------
><span data-ttu-id="33ac5-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="33ac5-123">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="33ac5-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="33ac5-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="33ac5-125">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="33ac5-125">See also</span></span>


[<span data-ttu-id="33ac5-126">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="33ac5-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)