---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: GetMetaConfiguration-Methode
ms.openlocfilehash: bd280cb8ebd7b0522e4e01cbd24bd9bdcfddf4c2
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953407"
---
# <a name="getmetaconfiguration-method"></a><span data-ttu-id="24061-103">GetMetaConfiguration-Methode</span><span class="sxs-lookup"><span data-stu-id="24061-103">GetMetaConfiguration method</span></span>

<span data-ttu-id="24061-104">Ruft die Einstellungen des lokalen Konfigurations-Managers ab, die zur Steuerung des Konfigurations-Agents verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="24061-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="24061-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="24061-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="24061-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="24061-106">Parameters</span></span>

<span data-ttu-id="24061-107">*MetaConfiguration* \[out\] Enthält bei der Rückgabe eine eingebettete Instanz der **MSFT_DSCMetaConfiguration**-Klasse, die die Einstellungen definiert.</span><span class="sxs-lookup"><span data-stu-id="24061-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="24061-108">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="24061-108">Return value</span></span>

<span data-ttu-id="24061-109">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="24061-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="24061-110">Hinweise</span><span class="sxs-lookup"><span data-stu-id="24061-110">Remarks</span></span>

<span data-ttu-id="24061-111">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="24061-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="24061-112">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="24061-112">Requirements</span></span>

<span data-ttu-id="24061-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="24061-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="24061-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="24061-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="24061-115">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="24061-115">See also</span></span>

[<span data-ttu-id="24061-116">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="24061-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
