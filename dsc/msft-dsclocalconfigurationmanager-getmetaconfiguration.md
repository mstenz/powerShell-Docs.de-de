---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: GetMetaConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: ddc016402239bcdea060a717fbac9ab7ea42698c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="51a10-103">GetMetaConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="51a10-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="51a10-104">Ruft die Einstellungen des lokalen Konfigurations-Managers ab, die zur Steuerung des Konfigurations-Agents verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="51a10-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="51a10-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="51a10-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="51a10-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="51a10-106">Parameters</span></span>
----------

<span data-ttu-id="51a10-107">*MetaConfiguration* \[out\] Enthält bei der Rückgabe eine eingebettete Instanz der **MSFT_DSCMetaConfiguration**-Klasse, die die Einstellungen definiert.</span><span class="sxs-lookup"><span data-stu-id="51a10-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="51a10-108">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="51a10-108">Return value</span></span>
------------

<span data-ttu-id="51a10-109">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="51a10-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="51a10-110">Hinweise</span><span class="sxs-lookup"><span data-stu-id="51a10-110">Remarks</span></span>

<span data-ttu-id="51a10-111">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="51a10-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="51a10-112">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="51a10-112">Requirements</span></span>
------------
><span data-ttu-id="51a10-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="51a10-113">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="51a10-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="51a10-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="51a10-115">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="51a10-115">See also</span></span>


[<span data-ttu-id="51a10-116">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="51a10-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)