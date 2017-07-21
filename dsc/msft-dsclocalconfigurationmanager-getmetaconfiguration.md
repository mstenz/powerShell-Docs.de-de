---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: GetMetaConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 4f209014e9fde5841a9bce743f5364e6677d1e41
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="1ef1c-103">GetMetaConfiguration-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="1ef1c-103">GetMetaConfiguration method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="1ef1c-104">Ruft die Einstellungen des lokalen Konfigurations-Managers ab, die zur Steuerung des Konfigurations-Agents verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-104">Gets the local Configuration Manager settings that are used to control the Configuration Agent.</span></span>

<a name="syntax"></a><span data-ttu-id="1ef1c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1ef1c-105">Syntax</span></span>
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a name="parameters"></a><span data-ttu-id="1ef1c-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="1ef1c-106">Parameters</span></span>
----------

<span data-ttu-id="1ef1c-107">*MetaConfiguration* \[out\]</span><span class="sxs-lookup"><span data-stu-id="1ef1c-107">*MetaConfiguration* \[out\]</span></span>  
<span data-ttu-id="1ef1c-108">Enthält bei der Rückgabe eine eingebettete Instanz der **MSFT_DSCMetaConfiguration**-Klasse, die die Einstellungen definiert.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-108">On return, contains an embedded instance of the **MSFT_DSCMetaConfiguration** class that defines the settings.</span></span>

## <a name="return-value"></a><span data-ttu-id="1ef1c-109">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="1ef1c-109">Return value</span></span>
------------

<span data-ttu-id="1ef1c-110">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-110">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="1ef1c-111">Hinweise</span><span class="sxs-lookup"><span data-stu-id="1ef1c-111">Remarks</span></span>

<span data-ttu-id="1ef1c-112">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="1ef1c-112">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="1ef1c-113">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="1ef1c-113">Requirements</span></span>
------------
><span data-ttu-id="1ef1c-114">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="1ef1c-114">**MOF:** DscCore.mof</span></span>

><span data-ttu-id="1ef1c-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="1ef1c-115">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>


## <a name="see-also"></a><span data-ttu-id="1ef1c-116">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="1ef1c-116">See also</span></span>


[<span data-ttu-id="1ef1c-117">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="1ef1c-117">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)


 

 



