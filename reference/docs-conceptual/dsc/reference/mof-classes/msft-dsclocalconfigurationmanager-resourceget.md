---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: ResourceGet-Methode
ms.openlocfilehash: dbe610dfcef5ef6c79783801ecb6fdb7408bdfa5
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954997"
---
# <a name="resourceget-method"></a><span data-ttu-id="24277-103">ResourceGet-Methode</span><span class="sxs-lookup"><span data-stu-id="24277-103">ResourceGet method</span></span>

<span data-ttu-id="24277-104">Ruft direkt die **Get**-Methode einer DSC-Ressource auf.</span><span class="sxs-lookup"><span data-stu-id="24277-104">Directly calls the **Get** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="24277-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="24277-105">Syntax</span></span>

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a><span data-ttu-id="24277-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="24277-106">Parameters</span></span>

<span data-ttu-id="24277-107">*ResourceType* \[in\] Der Name der aufzurufenden Ressource.</span><span class="sxs-lookup"><span data-stu-id="24277-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="24277-108">*ModuleName* \[in\] Der Name des Moduls, das die aufzurufende Ressource enthält.</span><span class="sxs-lookup"><span data-stu-id="24277-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="24277-109">*resourceProperty* \[in\] Gibt den Namen der Ressourceneigenschaft und deren Wert in einer Hashtabelle als Schlüssel und Wert an.</span><span class="sxs-lookup"><span data-stu-id="24277-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="24277-110">Verwenden Sie das Cmdlet [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) zum Ermitteln von Ressourceneigenschaften und deren Typen.</span><span class="sxs-lookup"><span data-stu-id="24277-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="24277-111">*configurations* \[out\] Enthält bei Rückgabe eine eingebettete Instanz der Konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="24277-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="24277-112">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="24277-112">Return value</span></span>

<span data-ttu-id="24277-113">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="24277-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="24277-114">Hinweise</span><span class="sxs-lookup"><span data-stu-id="24277-114">Remarks</span></span>

<span data-ttu-id="24277-115">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="24277-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="24277-116">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="24277-116">Requirements</span></span>

<span data-ttu-id="24277-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="24277-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="24277-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="24277-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="24277-119">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="24277-119">See also</span></span>

[<span data-ttu-id="24277-120">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="24277-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)
