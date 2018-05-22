---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: GetConfigurationStatus-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 725b1a2a62510a4e9b59aabdec8a7e502c737bfc
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2018
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="48260-103">GetConfigurationStatus-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="48260-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="48260-104">Abrufen des Konfigurationsstatusverlaufs.</span><span class="sxs-lookup"><span data-stu-id="48260-104">Get the configuration status history.</span></span>

<a name="syntax"></a><span data-ttu-id="48260-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="48260-105">Syntax</span></span>
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a><span data-ttu-id="48260-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="48260-106">Parameters</span></span>
----------

<span data-ttu-id="48260-107">*All* \[in\] **true**, wenn diese Methode Informationen zu allen Konfigurationsausführungen auf dem Computer zurückgeben soll, einschließlich der Konfigurationsanwendung und der Konsistenzprüfung.</span><span class="sxs-lookup"><span data-stu-id="48260-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="48260-108">*configurationStatus* \[out\] Enthält bei der Rückgabe eine eingebettete Instanz der **MSFT_DSCConfigurationStatus**-Klasse, die die Einstellungen definiert.</span><span class="sxs-lookup"><span data-stu-id="48260-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="48260-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="48260-109">Return value</span></span>
------------

<span data-ttu-id="48260-110">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="48260-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="48260-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="48260-111">Remarks</span></span>

<span data-ttu-id="48260-112">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="48260-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="48260-113">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="48260-113">Requirements</span></span>
------------
><span data-ttu-id="48260-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="48260-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="48260-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="48260-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="48260-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="48260-116">See also</span></span>


[<span data-ttu-id="48260-117">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="48260-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)