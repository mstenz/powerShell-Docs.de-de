---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: RemoveConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: fed45836293adedbce18f01cfe53cdfa1a474975
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="f3a84-103">RemoveConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="f3a84-103">RemoveConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="f3a84-104">Entfernt die Konfigurationsdateien.</span><span class="sxs-lookup"><span data-stu-id="f3a84-104">Removes the configuration files.</span></span>

<a name="syntax"></a><span data-ttu-id="f3a84-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f3a84-105">Syntax</span></span>
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a><span data-ttu-id="f3a84-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="f3a84-106">Parameters</span></span>
----------

<span data-ttu-id="f3a84-107">*Stage* \[in\]</span><span class="sxs-lookup"><span data-stu-id="f3a84-107">*Stage* \[in\]</span></span>  
<span data-ttu-id="f3a84-108">Gibt an, welches Konfigurationsdokument entfernt werden soll.</span><span class="sxs-lookup"><span data-stu-id="f3a84-108">Specifies which configuration document to remove.</span></span> <span data-ttu-id="f3a84-109">Die folgenden Werte sind gültig:</span><span class="sxs-lookup"><span data-stu-id="f3a84-109">The following values are valid:</span></span>

|<span data-ttu-id="f3a84-110">Wert</span><span class="sxs-lookup"><span data-stu-id="f3a84-110">Value</span></span> |<span data-ttu-id="f3a84-111">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="f3a84-111">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="f3a84-112">**1**</span><span class="sxs-lookup"><span data-stu-id="f3a84-112">**1**</span></span> | <span data-ttu-id="f3a84-113">Das **aktuelle** (Current) Konfigurationsdokument (current.mof).</span><span class="sxs-lookup"><span data-stu-id="f3a84-113">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="f3a84-114">**2**</span><span class="sxs-lookup"><span data-stu-id="f3a84-114">**2**</span></span> | <span data-ttu-id="f3a84-115">Das **ausstehende** (Pending) Konfigurationsdokument (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="f3a84-115">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="f3a84-116">**4**</span><span class="sxs-lookup"><span data-stu-id="f3a84-116">**4**</span></span> | <span data-ttu-id="f3a84-117">Das **vorherige** (Previous) Konfigurationsdokument (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="f3a84-117">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="f3a84-118">*Force* \[in\]</span><span class="sxs-lookup"><span data-stu-id="f3a84-118">*Force* \[in\]</span></span>  
<span data-ttu-id="f3a84-119">**true**, um das Entfernen der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="f3a84-119">**true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="f3a84-120">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="f3a84-120">Return value</span></span>
------------

<span data-ttu-id="f3a84-121">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="f3a84-121">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f3a84-122">Hinweise</span><span class="sxs-lookup"><span data-stu-id="f3a84-122">Remarks</span></span>

<span data-ttu-id="f3a84-123">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="f3a84-123">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f3a84-124">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="f3a84-124">Requirements</span></span>
------------
><span data-ttu-id="f3a84-125">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f3a84-125">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="f3a84-126">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f3a84-126">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="f3a84-127">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f3a84-127">See also</span></span>


[<span data-ttu-id="f3a84-128">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="f3a84-128">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



