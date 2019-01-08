---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: ResourceSet-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: 2712b7ff0a19e643c1f343d436c084f8970c9dd4
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047328"
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="8944c-103">ResourceSet-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="8944c-103">ResourceSet method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="8944c-104">Ruft direkt die **Set**-Methode einer DSC-Ressource auf.</span><span class="sxs-lookup"><span data-stu-id="8944c-104">Directly calls the **Set** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="8944c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="8944c-105">Syntax</span></span>

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a><span data-ttu-id="8944c-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="8944c-106">Parameters</span></span>

<span data-ttu-id="8944c-107">*ResourceType* \[in\] Der Name der aufzurufenden Ressource.</span><span class="sxs-lookup"><span data-stu-id="8944c-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="8944c-108">*ModuleName* \[in\] Der Name des Moduls, das die aufzurufende Ressource enthält.</span><span class="sxs-lookup"><span data-stu-id="8944c-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="8944c-109">*resourceProperty* \[in\] Gibt den Namen der Ressourceneigenschaft und deren Wert in einer Hashtabelle als Schlüssel und Wert an.</span><span class="sxs-lookup"><span data-stu-id="8944c-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="8944c-110">Verwenden Sie das Cmdlet [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) zum Ermitteln von Ressourceneigenschaften und deren Typen.</span><span class="sxs-lookup"><span data-stu-id="8944c-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="8944c-111">*RebootRequired* \[out\] Bei der Rückgabe wird diese Eigenschaft auf **true** festgelegt, wenn der Zielknoten neu gestartet werden muss.</span><span class="sxs-lookup"><span data-stu-id="8944c-111">*RebootRequired* \[out\] On return, this property is set to **true** if the target node needs to be rebooted.</span></span>

## <a name="return-value"></a><span data-ttu-id="8944c-112">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="8944c-112">Return value</span></span>

<span data-ttu-id="8944c-113">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="8944c-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="8944c-114">Hinweise</span><span class="sxs-lookup"><span data-stu-id="8944c-114">Remarks</span></span>

<span data-ttu-id="8944c-115">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="8944c-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="8944c-116">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="8944c-116">Requirements</span></span>

<span data-ttu-id="8944c-117">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="8944c-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="8944c-118">\*\*Namespace: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="8944c-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="8944c-119">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="8944c-119">See also</span></span>

[<span data-ttu-id="8944c-120">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="8944c-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)