---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: GetMetaConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: e14237ef68b95d68e2f14071aa1fa6ba0717f39f
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047805"
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="f86c9-103">GetMetaConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="f86c9-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="f86c9-104">Ruft die Einstellungen des lokalen Konfigurations-Managers ab, die zur Steuerung des Konfigurations-Agents verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="f86c9-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

## <a name="syntax"></a><span data-ttu-id="f86c9-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f86c9-105">Syntax</span></span>

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

## <a name="parameters"></a><span data-ttu-id="f86c9-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="f86c9-106">Parameters</span></span>

<span data-ttu-id="f86c9-107">*MetaConfiguration* \[out\] Enthält bei der Rückgabe eine eingebettete Instanz der **MSFT_DSCMetaConfiguration**-Klasse, die die Einstellungen definiert.</span><span class="sxs-lookup"><span data-stu-id="f86c9-107">*MetaConfiguration* \[out\] On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="f86c9-108">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="f86c9-108">Return value</span></span>

<span data-ttu-id="f86c9-109">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="f86c9-109">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f86c9-110">Hinweise</span><span class="sxs-lookup"><span data-stu-id="f86c9-110">Remarks</span></span>

<span data-ttu-id="f86c9-111">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="f86c9-111">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="f86c9-112">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="f86c9-112">Requirements</span></span>

<span data-ttu-id="f86c9-113">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="f86c9-113">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="f86c9-114">\*\*Namespace: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="f86c9-114">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="f86c9-115">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f86c9-115">See also</span></span>

[<span data-ttu-id="f86c9-116">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="f86c9-116">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)