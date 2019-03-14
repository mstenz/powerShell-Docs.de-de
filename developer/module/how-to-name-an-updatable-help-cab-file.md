---
title: 'Gewusst wie: Benennen Sie eine aktualisierbare Hilfe CAB-Datei | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: 0b58d5ee19a85bed26bc6549ced48b890cd62f64
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2019
ms.locfileid: "57794756"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="202af-102">Benennen von aktualisierbaren CAB-Hilfedateien</span><span class="sxs-lookup"><span data-stu-id="202af-102">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="202af-103">In diesem Thema wird erläutert, das erforderliche Format für die aktualisierbare Hilfe CAB-Datei (. CAB-Datei)-Dateien.</span><span class="sxs-lookup"><span data-stu-id="202af-103">This topic explains the required name format for the Updatable Help cabinet (.CAB) files.</span></span>

## <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="202af-104">Benennen von aktualisierbaren CAB-Hilfedateien</span><span class="sxs-lookup"><span data-stu-id="202af-104">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="202af-105">Aktualisierbare CAB-Datei (. CAB-Datei)-Datei muss es sich um einen Namen mit dem folgenden Format aufweisen.</span><span class="sxs-lookup"><span data-stu-id="202af-105">A Updatable cabinet (.CAB) file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

<span data-ttu-id="202af-106">Die Elemente mit dem Namen sind wie folgt aus.</span><span class="sxs-lookup"><span data-stu-id="202af-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="202af-107">ModuleName den Wert von der **Namen** Eigenschaft der **ModuleInfo** -Objekt, die [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) -Cmdlet wird zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="202af-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="202af-108">ModuleGUID den Wert von der **GUID** -Schlüssels im modulmanifest.</span><span class="sxs-lookup"><span data-stu-id="202af-108">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="202af-109">Der UICulture-UI-Kultur der Hilfedateien in der CAB-Datei.</span><span class="sxs-lookup"><span data-stu-id="202af-109">UICulture The UI culture of the help files in the CAB file.</span></span> <span data-ttu-id="202af-110">Dieser Wert muss dem Wert eines entsprechen den **UICulture** Elemente in der HelpInfo-XML-Datendatei für das Modul.</span><span class="sxs-lookup"><span data-stu-id="202af-110">This value must match the value of one of the **UICulture** elements in the HelpInfo XML file for the module.</span></span>

<span data-ttu-id="202af-111">Beispielsweise ist der Modulname "TestModule", die Modul-GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, und die UI-Kultur ist "En-US", der Namen der CAB-Datei:</span><span class="sxs-lookup"><span data-stu-id="202af-111">For example, if the module name is "TestModule," the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, and the UI culture is "en-US", the name of the CAB file would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`