---
title: 'Gewusst wie: Benennen Sie eine HelpInfo-XML-Datei | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 64e85b53-5aeb-4d6c-903c-af4ab62f11c1
caps.latest.revision: 7
ms.openlocfilehash: a3e8ae664d5c0e29d0f84174950bebe6a1da6a81
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857826"
---
# <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="5640e-102">Benennen einer XML-Datei HelpInfo</span><span class="sxs-lookup"><span data-stu-id="5640e-102">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="5640e-103">In diesem Thema wird erläutert, das Format der erforderliche Name für die aktualisierbare Hilfe-Informationen-Dateien, die so genannte HelpInfo XML-Dateien.</span><span class="sxs-lookup"><span data-stu-id="5640e-103">This topic explains the required name format for the Updatable Help Information files, commonly known as HelpInfo XML files.</span></span>

## <a name="how-to-name-a-helpinfo-xml-file"></a><span data-ttu-id="5640e-104">Benennen einer XML-Datei HelpInfo</span><span class="sxs-lookup"><span data-stu-id="5640e-104">How to Name a HelpInfo XML File</span></span>

<span data-ttu-id="5640e-105">Eine HelpInfo XML-Datei muss es sich um einen Namen mit dem folgenden Format haben.</span><span class="sxs-lookup"><span data-stu-id="5640e-105">A HelpInfo XML file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_HelpInfo.xml`

<span data-ttu-id="5640e-106">Die Elemente mit dem Namen sind wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="5640e-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="5640e-107">ModuleName den Wert von der **Namen** Eigenschaft der **ModuleInfo** -Objekt, die [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) -Cmdlet wird zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="5640e-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>
<span data-ttu-id="5640e-108">Der Wert des der **Namen** Eigenschaft der **ModuleInfo** -Objekt, die [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) -Cmdlet zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="5640e-108">The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="5640e-109">ModuleGUID den Wert von der **GUID** -Schlüssels im modulmanifest.</span><span class="sxs-lookup"><span data-stu-id="5640e-109">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="5640e-110">Beispielsweise wäre wenn "TestModule" ist, und die Modul-GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9 ist, der Namen der HelpInfo XML-Datei für das Modul:</span><span class="sxs-lookup"><span data-stu-id="5640e-110">For example, if the module name is "TestModule" and the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, the name of the HelpInfo XML file for the module would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_HelpInfo.xml`