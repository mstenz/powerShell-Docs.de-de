---
ms.date: 06/12/2017
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: RemoveConfiguration-Methode
ms.openlocfilehash: aacbed96beb960d7e0d449423a4de9a27f0a287e
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953397"
---
# <a name="removeconfiguration-method"></a><span data-ttu-id="5ebf6-103">RemoveConfiguration-Methode</span><span class="sxs-lookup"><span data-stu-id="5ebf6-103">RemoveConfiguration method</span></span>

<span data-ttu-id="5ebf6-104">Entfernt die Konfigurationsdateien.</span><span class="sxs-lookup"><span data-stu-id="5ebf6-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="5ebf6-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5ebf6-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="5ebf6-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="5ebf6-106">Parameters</span></span>

<span data-ttu-id="5ebf6-107">*Stage* \[in\] Gibt an, welches Konfigurationsdokument entfernt werden soll.</span><span class="sxs-lookup"><span data-stu-id="5ebf6-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="5ebf6-108">Die folgenden Werte sind gültig:</span><span class="sxs-lookup"><span data-stu-id="5ebf6-108">The following values are valid:</span></span>

|<span data-ttu-id="5ebf6-109">Wert</span><span class="sxs-lookup"><span data-stu-id="5ebf6-109">Value</span></span> |<span data-ttu-id="5ebf6-110">BESCHREIBUNG</span><span class="sxs-lookup"><span data-stu-id="5ebf6-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="5ebf6-111">**1**</span><span class="sxs-lookup"><span data-stu-id="5ebf6-111">**1**</span></span> | <span data-ttu-id="5ebf6-112">Das **aktuelle** (Current) Konfigurationsdokument (current.mof).</span><span class="sxs-lookup"><span data-stu-id="5ebf6-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="5ebf6-113">**2**</span><span class="sxs-lookup"><span data-stu-id="5ebf6-113">**2**</span></span> | <span data-ttu-id="5ebf6-114">Das **ausstehende** (Pending) Konfigurationsdokument (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="5ebf6-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="5ebf6-115">**4**</span><span class="sxs-lookup"><span data-stu-id="5ebf6-115">**4**</span></span> | <span data-ttu-id="5ebf6-116">Das **vorherige** (Previous) Konfigurationsdokument (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="5ebf6-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="5ebf6-117">*Force* \[in\] **true**, um das Entfernen der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="5ebf6-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="5ebf6-118">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="5ebf6-118">Return value</span></span>

<span data-ttu-id="5ebf6-119">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="5ebf6-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5ebf6-120">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="5ebf6-120">Remarks</span></span>

<span data-ttu-id="5ebf6-121">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="5ebf6-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="5ebf6-122">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="5ebf6-122">Requirements</span></span>

<span data-ttu-id="5ebf6-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="5ebf6-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="5ebf6-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="5ebf6-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="5ebf6-125">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="5ebf6-125">See also</span></span>

[<span data-ttu-id="5ebf6-126">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="5ebf6-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
