---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: RemoveConfiguration-Methode
ms.openlocfilehash: aacbed96beb960d7e0d449423a4de9a27f0a287e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953397"
---
# <a name="removeconfiguration-method"></a><span data-ttu-id="c4c69-103">RemoveConfiguration-Methode</span><span class="sxs-lookup"><span data-stu-id="c4c69-103">RemoveConfiguration method</span></span>

<span data-ttu-id="c4c69-104">Entfernt die Konfigurationsdateien.</span><span class="sxs-lookup"><span data-stu-id="c4c69-104">Removes the configuration files.</span></span>

## <a name="syntax"></a><span data-ttu-id="c4c69-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c4c69-105">Syntax</span></span>

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a><span data-ttu-id="c4c69-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="c4c69-106">Parameters</span></span>

<span data-ttu-id="c4c69-107">*Stage* \[in\] Gibt an, welches Konfigurationsdokument entfernt werden soll.</span><span class="sxs-lookup"><span data-stu-id="c4c69-107">*Stage* \[in\] Specifies which configuration document to remove.</span></span> <span data-ttu-id="c4c69-108">Die folgenden Werte sind gültig:</span><span class="sxs-lookup"><span data-stu-id="c4c69-108">The following values are valid:</span></span>

|<span data-ttu-id="c4c69-109">Wert</span><span class="sxs-lookup"><span data-stu-id="c4c69-109">Value</span></span> |<span data-ttu-id="c4c69-110">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c4c69-110">Description</span></span> |
|:--- |:---|
|<span data-ttu-id="c4c69-111">**1**</span><span class="sxs-lookup"><span data-stu-id="c4c69-111">**1**</span></span> | <span data-ttu-id="c4c69-112">Das **aktuelle** (Current) Konfigurationsdokument (current.mof).</span><span class="sxs-lookup"><span data-stu-id="c4c69-112">The **Current** configuration document (current.mof).</span></span> |
|<span data-ttu-id="c4c69-113">**2**</span><span class="sxs-lookup"><span data-stu-id="c4c69-113">**2**</span></span> | <span data-ttu-id="c4c69-114">Das **ausstehende** (Pending) Konfigurationsdokument (pending.mof).</span><span class="sxs-lookup"><span data-stu-id="c4c69-114">The **Pending** configuration document (pending.mof).</span></span>  |
|<span data-ttu-id="c4c69-115">**4**</span><span class="sxs-lookup"><span data-stu-id="c4c69-115">**4**</span></span> | <span data-ttu-id="c4c69-116">Das **vorherige** (Previous) Konfigurationsdokument (previous.mof).</span><span class="sxs-lookup"><span data-stu-id="c4c69-116">The **Previous** configuration document (previous.mof).</span></span> |

<span data-ttu-id="c4c69-117">*Force* \[in\] **true**, um das Entfernen der Konfiguration zu erzwingen.</span><span class="sxs-lookup"><span data-stu-id="c4c69-117">*Force* \[in\] **true** to force the removal of the configuration.</span></span>

## <a name="return-value"></a><span data-ttu-id="c4c69-118">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="c4c69-118">Return value</span></span>

<span data-ttu-id="c4c69-119">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="c4c69-119">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="c4c69-120">Hinweise</span><span class="sxs-lookup"><span data-stu-id="c4c69-120">Remarks</span></span>

<span data-ttu-id="c4c69-121">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="c4c69-121">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="c4c69-122">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="c4c69-122">Requirements</span></span>

<span data-ttu-id="c4c69-123">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="c4c69-123">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="c4c69-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="c4c69-124">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="c4c69-125">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c4c69-125">See also</span></span>

[<span data-ttu-id="c4c69-126">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="c4c69-126">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
