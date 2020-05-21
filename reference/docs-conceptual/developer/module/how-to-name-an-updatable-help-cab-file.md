---
title: Benennen der CAB-Datei für eine aktualisierbare Hilfe | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: de302da0-c17a-4d31-a8ef-14a626738993
caps.latest.revision: 7
ms.openlocfilehash: a253f98d213f797a659affb1560907bb99a045d3
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560558"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="530dd-102">Benennen von aktualisierbaren CAB-Hilfedateien</span><span class="sxs-lookup"><span data-stu-id="530dd-102">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="530dd-103">In diesem Thema wird das erforderliche Namensformat für den aktualisierbaren Hilfe Schrank () erläutert. CAB-Dateien.</span><span class="sxs-lookup"><span data-stu-id="530dd-103">This topic explains the required name format for the Updatable Help cabinet (.CAB) files.</span></span>

## <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="530dd-104">Benennen von aktualisierbaren CAB-Hilfedateien</span><span class="sxs-lookup"><span data-stu-id="530dd-104">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="530dd-105">Eine aktualisierbare CAB-(. CAB) muss ein Name im folgenden Format vorliegen.</span><span class="sxs-lookup"><span data-stu-id="530dd-105">A Updatable cabinet (.CAB) file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

<span data-ttu-id="530dd-106">Die Elemente des Namens lauten wie folgt.</span><span class="sxs-lookup"><span data-stu-id="530dd-106">The elements of the name are as follows.</span></span>

<span data-ttu-id="530dd-107">ModuleName der Wert der **Name** -Eigenschaft des **ModuleInfo** -Objekts, das vom [Get-Module-](/powershell/module/Microsoft.PowerShell.Core/Get-Module) Cmdlet zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="530dd-107">ModuleName The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>

<span data-ttu-id="530dd-108">ModuleGUID der Wert des **GUID** -Schlüssels im Modul Manifest.</span><span class="sxs-lookup"><span data-stu-id="530dd-108">ModuleGUID The value of the **GUID** key in the module manifest.</span></span>

<span data-ttu-id="530dd-109">UICulture die Benutzeroberflächen Kultur der Hilfedateien in der CAB-Datei.</span><span class="sxs-lookup"><span data-stu-id="530dd-109">UICulture The UI culture of the help files in the CAB file.</span></span> <span data-ttu-id="530dd-110">Dieser Wert muss mit dem Wert eines der **UICulture** -Elemente in der helpinfo-XML-Datei für das Modul identisch sein.</span><span class="sxs-lookup"><span data-stu-id="530dd-110">This value must match the value of one of the **UICulture** elements in the HelpInfo XML file for the module.</span></span>

<span data-ttu-id="530dd-111">Wenn der Modulname beispielsweise "Testmodule" lautet, ist die Modul-GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, und die Benutzeroberflächen Kultur ist "en-US", der Name der CAB-Datei lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="530dd-111">For example, if the module name is "TestModule," the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, and the UI culture is "en-US", the name of the CAB file would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`
