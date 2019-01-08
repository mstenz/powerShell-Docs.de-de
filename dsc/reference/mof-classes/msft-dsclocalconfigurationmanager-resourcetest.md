---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: ResourceTest-Methode der MSFT_DSCLocalConfigurationManager-Klasse
ms.openlocfilehash: e7645b0c6b93b96cb01f72c1c92d468f7642ea13
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047341"
---
# <a name="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class"></a><span data-ttu-id="7e204-103">ResourceTest-Methode der MSFT_DSCLocalConfigurationManager-Klasse</span><span class="sxs-lookup"><span data-stu-id="7e204-103">ResourceTest method of the MSFT_DSCLocalConfigurationManager class</span></span>

<span data-ttu-id="7e204-104">Ruft direkt die **Test**-Methode einer DSC-Ressource auf.</span><span class="sxs-lookup"><span data-stu-id="7e204-104">Directly calls the **Test** method of a DSC resource.</span></span>

## <a name="syntax"></a><span data-ttu-id="7e204-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7e204-105">Syntax</span></span>

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

## <a name="parameters"></a><span data-ttu-id="7e204-106">Parameter</span><span class="sxs-lookup"><span data-stu-id="7e204-106">Parameters</span></span>

<span data-ttu-id="7e204-107">*ResourceType* \[in\] Der Name der aufzurufenden Ressource.</span><span class="sxs-lookup"><span data-stu-id="7e204-107">*ResourceType* \[in\] The name of the resource to call.</span></span>

<span data-ttu-id="7e204-108">*ModuleName* \[in\] Der Name des Moduls, das die aufzurufende Ressource enthält.</span><span class="sxs-lookup"><span data-stu-id="7e204-108">*ModuleName* \[in\] The name of the module that contains the resource to call.</span></span>

<span data-ttu-id="7e204-109">*resourceProperty* \[in\] Gibt den Namen der Ressourceneigenschaft und deren Wert in einer Hashtabelle als Schlüssel und Wert an.</span><span class="sxs-lookup"><span data-stu-id="7e204-109">*resourceProperty* \[in\] Specifies the resource property name and its value in a hash table as key and value, respectively.</span></span> <span data-ttu-id="7e204-110">Verwenden Sie das Cmdlet [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) zum Ermitteln von Ressourceneigenschaften und deren Typen.</span><span class="sxs-lookup"><span data-stu-id="7e204-110">Use the [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) cmdlet to discover resource properties and their types.</span></span>

<span data-ttu-id="7e204-111">*InDesiredState* \[out\] Bei der Rückgabe wird diese Eigenschaft auf **true** festgelegt, wenn sich der Zielknoten im gewünschten Zustand befindet.</span><span class="sxs-lookup"><span data-stu-id="7e204-111">*InDesiredState* \[out\] On return, this property is set to **true** if the target node is in the desired state.</span></span>

## <a name="return-value"></a><span data-ttu-id="7e204-112">Rückgabewert</span><span class="sxs-lookup"><span data-stu-id="7e204-112">Return value</span></span>

<span data-ttu-id="7e204-113">Gibt bei Erfolg null zurück, andernfalls einen Fehlercode.</span><span class="sxs-lookup"><span data-stu-id="7e204-113">Returns zero on success; otherwise returns an error code.</span></span>

## <a name="remarks"></a><span data-ttu-id="7e204-114">Hinweise</span><span class="sxs-lookup"><span data-stu-id="7e204-114">Remarks</span></span>

<span data-ttu-id="7e204-115">Dies ist eine statische Methode.</span><span class="sxs-lookup"><span data-stu-id="7e204-115">This is a static method.</span></span>

## <a name="requirements"></a><span data-ttu-id="7e204-116">Anforderungen</span><span class="sxs-lookup"><span data-stu-id="7e204-116">Requirements</span></span>

<span data-ttu-id="7e204-117">MOF\*\* DscCore.mof</span><span class="sxs-lookup"><span data-stu-id="7e204-117">**MOF:** DscCore.mof</span></span>

<span data-ttu-id="7e204-118">\*\*Namespace: Root\Microsoft\Windows\DesiredStateConfiguration</span><span class="sxs-lookup"><span data-stu-id="7e204-118">**Namespace**: Root\Microsoft\Windows\DesiredStateConfiguration</span></span>

## <a name="see-also"></a><span data-ttu-id="7e204-119">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="7e204-119">See also</span></span>

[<span data-ttu-id="7e204-120">**MSFT_DSCLocalConfigurationManager-Klasse**</span><span class="sxs-lookup"><span data-stu-id="7e204-120">**MSFT_DSCLocalConfigurationManager**</span></span>](msft-dsclocalconfigurationmanager.md)