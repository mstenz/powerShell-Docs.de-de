---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: GetConfigurationStatus-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: a41e7a15fc935c2cd5fd4cb66d0ab13509d5d4e0
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2018
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="959df-103">GetConfigurationStatus-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="959df-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="959df-104">Abrufen des Konfigurationsstatusverlaufs.</span><span class="sxs-lookup"><span data-stu-id="959df-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="959df-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="959df-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="959df-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="959df-106">Parameters</span></span>
----------

<span data-ttu-id="959df-107">*All* \[in\]</span><span class="sxs-lookup"><span data-stu-id="959df-107">*All* \[in\]</span></span>  
<span data-ttu-id="959df-108">**true**, wenn diese Methode Informationen zu allen Konfigurationsausführungen auf dem Computer zurückgeben soll, einschließlich der Konfigurationsanwendung und der Konsistenzprüfung.</span><span class="sxs-lookup"><span data-stu-id="959df-108">**true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="959df-109">*configurationStatus* \[out\]</span><span class="sxs-lookup"><span data-stu-id="959df-109">*configurationStatus* \[out\]</span></span>  
<span data-ttu-id="959df-110">Enthält bei der Rückgabe eine eingebettete Instanz der **MSFT_DSCConfigurationStatus**-Klasse, die die Einstellungen definiert.</span><span class="sxs-lookup"><span data-stu-id="959df-110">On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="959df-111">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="959df-111">Return value</span></span>
------------

<span data-ttu-id="959df-112">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="959df-112">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="959df-113">Hinweise</span><span class="sxs-lookup"><span data-stu-id="959df-113">Remarks</span></span>

<span data-ttu-id="959df-114">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="959df-114">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="959df-115">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="959df-115">Requirements</span></span>
------------
><span data-ttu-id="959df-116">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="959df-116">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="959df-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="959df-117">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="959df-118">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="959df-118">See also</span></span>


[<span data-ttu-id="959df-119">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="959df-119">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



