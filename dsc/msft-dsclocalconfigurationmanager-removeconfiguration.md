---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: RemoveConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: faa113c442b80eea3ac474220b098b7d80ec50a8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="bbd43-103">RemoveConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="bbd43-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="bbd43-104">Entfernt die Konfigurationsdateien.</span><span class="sxs-lookup"><span data-stu-id="bbd43-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="bbd43-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="bbd43-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="bbd43-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="bbd43-106">Parameters</span></span>
----------

<span data-ttu-id="bbd43-107">*Stage* \[in\]</span><span class="sxs-lookup"><span data-stu-id="bbd43-107">*Stage* \[in\]</span></span>  
<span data-ttu-id="bbd43-108">Gibt an, welches Konfigurationsdokument entfernt werden soll.</span><span class="sxs-lookup"><span data-stu-id="bbd43-108">Specifies which configuration document to remove.</span></span> <span data-ttu-id="bbd43-109">Die folgenden Werte sind gültig:</span><span class="sxs-lookup"><span data-stu-id="bbd43-109">The following values are valid:</span></span>

|<span data-ttu-id="bbd43-110">Value</span><span class="sxs-lookup"><span data-stu-id="bbd43-110">Value</span></span> |<span data-ttu-id="bbd43-111">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bbd43-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="bbd43-112">**1**</span><span class="sxs-lookup"><span data-stu-id="bbd43-112">**1**</span></span> | <span data-ttu-id="bbd43-113">Das **aktuelle** (Current) Konfigurationsdokument (current.mof).</span><span class="sxs-lookup"><span data-stu-id="bbd43-113">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="bbd43-114">**2**</span><span class="sxs-lookup"><span data-stu-id="bbd43-114">**2**</span></span> | <span data-ttu-id="bbd43-115">Das **ausstehende** (Pending) Konfigurationsdokument (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="bbd43-115">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="bbd43-116">**4**</span><span class="sxs-lookup"><span data-stu-id="bbd43-116">**4**</span></span> | <span data-ttu-id="bbd43-117">Das **vorherige** (Previous) Konfigurationsdokument (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="bbd43-117">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="bbd43-118">*Force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="bbd43-118">*Force* \[in\]</span></span>  
<span data-ttu-id="bbd43-119">**true**, um das Entfernen der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="bbd43-119">**true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="bbd43-120">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="bbd43-120">Return value</span></span>
------------

<span data-ttu-id="bbd43-121">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="bbd43-121">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="bbd43-122">Hinweise</span><span class="sxs-lookup"><span data-stu-id="bbd43-122">Remarks</span></span>

<span data-ttu-id="bbd43-123">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="bbd43-123">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="bbd43-124">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="bbd43-124">Requirements</span></span>
------------
><span data-ttu-id="bbd43-125">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="bbd43-125">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="bbd43-126">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="bbd43-126">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="bbd43-127">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="bbd43-127">See also</span></span>


[<span data-ttu-id="bbd43-128">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="bbd43-128">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



