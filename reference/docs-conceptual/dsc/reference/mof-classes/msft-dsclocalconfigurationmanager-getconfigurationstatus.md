---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: GetConfigurationStatus-Methode
ms.openlocfilehash: 83b30ba2612d962fcf2fa658d07d18fb2d91ccc7
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71955017"
---
# <a name="getconfigurationstatus-method"></a><span data-ttu-id="c8603-103">GetConfigurationStatus-Methode</span><span class="sxs-lookup"><span data-stu-id="c8603-103">GetConfigurationStatus method</span></span>

<span data-ttu-id="c8603-104">Abrufen des Konfigurationsstatusverlaufs.</span><span class="sxs-lookup"><span data-stu-id="c8603-104">Get the configuration status history.</span></span>

## <a name="syntax"></a><span data-ttu-id="c8603-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c8603-105">Syntax</span></span>

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a><span data-ttu-id="c8603-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="c8603-106">Parameters</span></span>

<span data-ttu-id="c8603-107">*All* \[in\] **true**, wenn diese Methode Informationen zu allen Konfigurationsausführungen auf dem Computer zurückgeben soll, einschließlich der Konfigurationsanwendung und der Konsistenzprüfung.</span><span class="sxs-lookup"><span data-stu-id="c8603-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="c8603-108">*configurationStatus* \[out\] Enthält bei der Rückgabe eine eingebettete Instanz der **MSFT_DSCConfigurationStatus**-Klasse, die die Einstellungen definiert.</span><span class="sxs-lookup"><span data-stu-id="c8603-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="c8603-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="c8603-109">Return value</span></span>

<span data-ttu-id="c8603-110">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="c8603-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c8603-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="c8603-111">Remarks</span></span>

<span data-ttu-id="c8603-112">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="c8603-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c8603-113">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="c8603-113">Requirements</span></span>

<span data-ttu-id="c8603-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c8603-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="c8603-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c8603-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="c8603-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c8603-116">See also</span></span>

[<span data-ttu-id="c8603-117">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="c8603-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
