---
title: Benennen von aktualisierbaren CAB-Hilfedateien
ms.date: 09/12/2016
ms.openlocfilehash: 42486461d92f1f6fcff452a4539edf5be7a66f22
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892998"
---
# <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="05972-102">Benennen von aktualisierbaren CAB-Hilfedateien</span><span class="sxs-lookup"><span data-stu-id="05972-102">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="05972-103">In diesem Thema wird das erforderliche Namensformat für die aktualisierbaren Hilfe CAB- `.CAB` Dateien () erläutert.</span><span class="sxs-lookup"><span data-stu-id="05972-103">This topic explains the required name format for the Updatable Help cabinet (`.CAB`) files.</span></span>

## <a name="how-to-name-an-updatable-help-cab-file"></a><span data-ttu-id="05972-104">Benennen von aktualisierbaren CAB-Hilfedateien</span><span class="sxs-lookup"><span data-stu-id="05972-104">How to Name an Updatable Help CAB File</span></span>

<span data-ttu-id="05972-105">Eine aktualisierbare CAB- `.CAB` Datei () muss einen Namen haben, der das folgende Format hat.</span><span class="sxs-lookup"><span data-stu-id="05972-105">A Updatable cabinet (`.CAB`) file must have a name with the following format.</span></span>

`<ModuleName>_<ModuleGUID>_<UICulture>_HelpContent.cab`

<span data-ttu-id="05972-106">Die Elemente des Namens lauten wie folgt.</span><span class="sxs-lookup"><span data-stu-id="05972-106">The elements of the name are as follows.</span></span>

- <span data-ttu-id="05972-107">`<ModuleName>`: Der Wert der **Name** -Eigenschaft des **ModuleInfo** -Objekts, das vom [Get-Module-](/powershell/module/Microsoft.PowerShell.Core/Get-Module) Cmdlet zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="05972-107">`<ModuleName>` -The value of the **Name** property of the **ModuleInfo** object that the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet returns.</span></span>
- <span data-ttu-id="05972-108">`<ModuleGUID>`: Der Wert des **GUID** -Schlüssels im Modul Manifest.</span><span class="sxs-lookup"><span data-stu-id="05972-108">`<ModuleGUID>` - The value of the **GUID** key in the module manifest.</span></span>
- <span data-ttu-id="05972-109">`<UICulture>`: Die Benutzeroberflächen Kultur der Hilfedateien in der CAB-Datei.</span><span class="sxs-lookup"><span data-stu-id="05972-109">`<UICulture>` - The UI culture of the help files in the CAB file.</span></span> <span data-ttu-id="05972-110">Dieser Wert muss mit dem Wert eines der **UICulture** -Elemente in der helpinfo-XML-Datei für das Modul identisch sein.</span><span class="sxs-lookup"><span data-stu-id="05972-110">This value must match the value of one of the **UICulture** elements in the HelpInfo XML file for the module.</span></span>

<span data-ttu-id="05972-111">Wenn der Modulname beispielsweise "Testmodule" lautet, ist die Modul-GUID 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, und die Benutzeroberflächen Kultur ist "en-US", der Name der CAB-Datei lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="05972-111">For example, if the module name is "TestModule," the module GUID is 9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9, and the UI culture is "en-US", the name of the CAB file would be:</span></span>

`TestModule_9cabb9ad-f2ac-4914-a46b-bfc1bebf07f9_en-US_HelpContent.cab`
