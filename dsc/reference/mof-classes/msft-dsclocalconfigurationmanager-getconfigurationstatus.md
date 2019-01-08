---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: GetConfigurationStatus-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: c66ccc4eefaef2d0c3a68fa8a96c5abb9bda6e4c
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047383"
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="d4d09-103">GetConfigurationStatus-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="d4d09-103">GetConfigurationStatus method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="d4d09-104">Abrufen des Konfigurationsstatusverlaufs.</span><span class="sxs-lookup"><span data-stu-id="d4d09-104">Get the configuration status history.</span></span>

## <a name="syntax"></a><span data-ttu-id="d4d09-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d4d09-105">Syntax</span></span>

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a><span data-ttu-id="d4d09-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="d4d09-106">Parameters</span></span>

<span data-ttu-id="d4d09-107">*All* \[in\] **true**, wenn diese Methode Informationen zu allen Konfigurationsausführungen auf dem Computer zurückgeben soll, einschließlich der Konfigurationsanwendung und der Konsistenzprüfung.</span><span class="sxs-lookup"><span data-stu-id="d4d09-107">*All* \[in\] **true** if this method should return information about all the configuration runs on the machine, including the configuration application and the consistency check.</span></span>

<span data-ttu-id="d4d09-108">*configurationStatus* \[out\] Enthält bei der Rückgabe eine eingebettete Instanz der **MSFT_DSCConfigurationStatus**-Klasse, die die Einstellungen definiert.</span><span class="sxs-lookup"><span data-stu-id="d4d09-108">*configurationStatus* \[out\] On return, contains an embedded instance of the **MSFT_DSCConfigurationStatus** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="d4d09-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="d4d09-109">Return value</span></span>

<span data-ttu-id="d4d09-110">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="d4d09-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="d4d09-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="d4d09-111">Remarks</span></span>

<span data-ttu-id="d4d09-112">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="d4d09-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="d4d09-113">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="d4d09-113">Requirements</span></span>

<span data-ttu-id="d4d09-114">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="d4d09-114">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="d4d09-115">\*\*Namespace: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="d4d09-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="d4d09-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="d4d09-116">See also</span></span>

[<span data-ttu-id="d4d09-117">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="d4d09-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)