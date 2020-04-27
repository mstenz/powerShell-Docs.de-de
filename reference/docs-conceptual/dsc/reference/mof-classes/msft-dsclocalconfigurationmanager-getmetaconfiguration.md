---
ms.date: 06/12/2017
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: GetMetaConfiguration-Methode
ms.openlocfilehash: bd280cb8ebd7b0522e4e01cbd24bd9bdcfddf4c2
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953407"
---
# <a name="getmetaconfiguration-method"></a><span data-ttu-id="7a376-103">GetMetaConfiguration-Methode</span><span class="sxs-lookup"><span data-stu-id="7a376-103">GetMetaConfiguration method</span></span>

<span data-ttu-id="7a376-104">Ruft die Einstellungen des lokalen Konfigurations-Managers ab, die zur Steuerung des Konfigurations-Agents verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="7a376-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="7a376-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7a376-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="7a376-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="7a376-106">Parameters</span></span>

<span data-ttu-id="7a376-107">*MetaConfiguration* \[out\] Enthält bei der Rückgabe eine eingebettete Instanz der **MSFT_DSCMetaConfiguration**-Klasse, die die Einstellungen definiert.</span><span class="sxs-lookup"><span data-stu-id="7a376-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="7a376-108">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="7a376-108">Return value</span></span>

<span data-ttu-id="7a376-109">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="7a376-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7a376-110">Bemerkungen</span><span class="sxs-lookup"><span data-stu-id="7a376-110">Remarks</span></span>

<span data-ttu-id="7a376-111">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="7a376-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7a376-112">Requirements (Anforderungen)</span><span class="sxs-lookup"><span data-stu-id="7a376-112">Requirements</span></span>

<span data-ttu-id="7a376-113">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7a376-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="7a376-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7a376-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="7a376-115">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7a376-115">See also</span></span>

[<span data-ttu-id="7a376-116">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="7a376-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
