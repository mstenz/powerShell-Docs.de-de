---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: ResourceGet-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 1b74adf2327af2e0f9416f1d00eac4e3b75e9013
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078570"
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="67935-103">ResourceGet-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="67935-103">ResourceGet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="67935-104">Ruft direkt die **Get**-Methode einer DSC-Ressource auf.</span><span class="sxs-lookup"><span data-stu-id="67935-104">Directly calls the **Get** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="67935-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="67935-105">Syntax</span></span>

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a><span data-ttu-id="67935-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="67935-106">Parameters</span></span>

<span data-ttu-id="67935-107">*ResourceType* \[in\] Der Name der aufzurufenden Ressource.</span><span class="sxs-lookup"><span data-stu-id="67935-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="67935-108">*ModuleName* \[in\] Der Name des Moduls, das die aufzurufende Ressource enthält.</span><span class="sxs-lookup"><span data-stu-id="67935-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="67935-109">*resourceProperty* \[in\] Gibt den Namen der Ressourceneigenschaft und deren Wert in einer Hashtabelle als Schlüssel und Wert an.</span><span class="sxs-lookup"><span data-stu-id="67935-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="67935-110">Verwenden Sie das Cmdlet [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) zum Ermitteln von Ressourceneigenschaften und deren Typen.</span><span class="sxs-lookup"><span data-stu-id="67935-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="67935-111">*configurations* \[out\] Enthält bei Rückgabe eine eingebettete Instanz der Konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="67935-111">*configurations* \[out\] On return, contains an embedded instance of the configurations.</span></span>

## <a name="return-value"></a><span data-ttu-id="67935-112">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="67935-112">Return value</span></span>

<span data-ttu-id="67935-113">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="67935-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="67935-114">Hinweise</span><span class="sxs-lookup"><span data-stu-id="67935-114">Remarks</span></span>

<span data-ttu-id="67935-115">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="67935-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="67935-116">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="67935-116">Requirements</span></span>

<span data-ttu-id="67935-117">**MOF:** DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="67935-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="67935-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="67935-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="67935-119">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="67935-119">See also</span></span>

[<span data-ttu-id="67935-120">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="67935-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)