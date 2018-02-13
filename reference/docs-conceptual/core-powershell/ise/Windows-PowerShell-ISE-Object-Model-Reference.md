---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Referenz zum Windows PowerShell ISE-Objektmodell
ms.assetid: e1a9e7d1-0fd5-47de-8d9b-f1be1ed13b0c
ms.openlocfilehash: 624ddca3895ba3e24bf52a27babdb07e8714baae
ms.sourcegitcommit: 18e3bfae83ffe282d3fd1a45f5386f3b7250f0c0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2018
---
# <a name="windows-powershell-ise-object-model-reference"></a><span data-ttu-id="59f05-103">Referenz zum Windows PowerShell ISE-Objektmodell</span><span class="sxs-lookup"><span data-stu-id="59f05-103">Windows PowerShell ISE Object Model Reference</span></span>
  
## <a name="object-model-reference"></a><span data-ttu-id="59f05-104">Objektmodellreferenz</span><span class="sxs-lookup"><span data-stu-id="59f05-104">Object Model Reference</span></span>
 <span data-ttu-id="59f05-105">Dieser Abschnitt enthält eine Referenz für die zugrunde liegenden Klassen, die die verschiedenen Objekte in Windows PowerShell® Integrated Scripting Environment (ISE) definieren.</span><span class="sxs-lookup"><span data-stu-id="59f05-105">This section provides a reference on the underlying classes that define the various objects inWindows PowerShell® Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="59f05-106">Informationen dazu, wie Sie die Objekte in der Hierarchie angeordnet anzeigen, finden Sie unter [Die ISE-Objektmodellhierarchie](The-ISE-Object-Model-Hierarchy.md).</span><span class="sxs-lookup"><span data-stu-id="59f05-106">To see the objects organized in their hierarchy, see [The ISE Object Model Hierarchy](The-ISE-Object-Model-Hierarchy.md).</span></span>

 <span data-ttu-id="59f05-107">[The ISEAddOnTool Object (Das ISEAddOnTool-Objekt)](The-ISEAddOnTool-Object.md) Beispiele: $psISE.CurrentVisibleHorizontalTool, $psISE.CurrentVisibleVerticalTool.</span><span class="sxs-lookup"><span data-stu-id="59f05-107">[The ISEAddOnTool Object](The-ISEAddOnTool-Object.md) Examples: $psISE.CurrentVisibleHorizontalTool, $psISE.CurrentVisibleVerticalTool.</span></span>

 <span data-ttu-id="59f05-108">[The ISEAddOnTool Object (Das ISEAddOnTool-Objekt)](The-ISEAddOnTool-Object.md) [The ISEEditor Object (Das ISEEditor-Objekt)](The-ISEEditor-Object.md) Beispiele: $psISE.CurrentFile.Editor, $psISE.CurrentPowerShellTab.Output, $psISE.CurrentPowerShellTab.CommandPane.</span><span class="sxs-lookup"><span data-stu-id="59f05-108">[The ISEAddOnTool Object](The-ISEAddOnTool-Object.md) [The ISEEditor Object](The-ISEEditor-Object.md) Examples: $psISE.CurrentFile.Editor, $psISE.CurrentPowerShellTab.Output, $psISE.CurrentPowerShellTab.CommandPane.</span></span>

 <span data-ttu-id="59f05-109">[The ISEFile Object (Das ISEFile-Objekt)](The-ISEFile-Object.md) Beispiele: $psISE.CurrentFile, $psISE.PowerShellTabs.Files\[0\].</span><span class="sxs-lookup"><span data-stu-id="59f05-109">[The ISEFile Object](The-ISEFile-Object.md) Examples: $psISE.CurrentFile, $psISE.PowerShellTabs.Files\[0\].</span></span>

 <span data-ttu-id="59f05-110">[The ISEFileCollection Object (Das ISEFileCollection-Objekt)](The-ISEFileCollection-Object.md) Beispiele: $psISE.PowerShellTabs.Files.</span><span class="sxs-lookup"><span data-stu-id="59f05-110">[The ISEFileCollection Object](The-ISEFileCollection-Object.md) Examples: $psISE.PowerShellTabs.Files.</span></span>

 <span data-ttu-id="59f05-111">[The ISEMenuItem Object (Das ISEMenuItem-Objekt)](The-ISEMenuItem-Object.md) Beispiele: $psISE.CurrentPowerShellTab.AddOnsMenu, $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus\[0\].</span><span class="sxs-lookup"><span data-stu-id="59f05-111">[The ISEMenuItem Object](The-ISEMenuItem-Object.md) Examples: $psISE.CurrentPowerShellTab.AddOnsMenu , $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus\[0\].</span></span>

 <span data-ttu-id="59f05-112">[The ISEMenuItemCollection Object (Das ISEMenuItemCollection-Objekt)](The-ISEMenuItemCollection-Object.md) Beispiel: $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.</span><span class="sxs-lookup"><span data-stu-id="59f05-112">[The ISEMenuItemCollection Object](The-ISEMenuItemCollection-Object.md) Example: $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.</span></span>

 <span data-ttu-id="59f05-113">[The ISEOptions Object (Das ISEOptions-Objekt)](The-ISEOptions-Object.md) Beispiele: $psISE.Options, $psISE.Options.DefaultOptions.</span><span class="sxs-lookup"><span data-stu-id="59f05-113">[The ISEOptions Object](The-ISEOptions-Object.md) Examples: $psISE.Options, $psISE.Options.DefaultOptions.</span></span>

 <span data-ttu-id="59f05-114">[The ObjectModelRoot Object (Das ObjectModelRoot-Objekt)](The-ObjectModelRoot-Object.md) Beispiel: Das $psISE-Stammobjekt.</span><span class="sxs-lookup"><span data-stu-id="59f05-114">[The ObjectModelRoot Object](The-ObjectModelRoot-Object.md) Example: The root $psISE object.</span></span>

 <span data-ttu-id="59f05-115">[The PowerShellTab Object (Das PowerShellTab-Objekt)](The-PowerShellTab-Object.md) Beispiele: $psISE.CurrentPowerShellTab, $psISE.PowerShellTabs\[0\].</span><span class="sxs-lookup"><span data-stu-id="59f05-115">[The PowerShellTab Object](The-PowerShellTab-Object.md) Examples: $psISE.CurrentPowerShellTab, $psISE.PowerShellTabs\[0\].</span></span>

 <span data-ttu-id="59f05-116">[The PowerShellTabCollection Object (Das PowerShellTabCollection-Objekt)](The-PowerShellTabCollection-Object.md) Beispiel: $psISE.PowerShellTabs.</span><span class="sxs-lookup"><span data-stu-id="59f05-116">[The PowerShellTabCollection Object](The-PowerShellTabCollection-Object.md) Example: $psISE.PowerShellTabs.</span></span>

## <a name="see-also"></a><span data-ttu-id="59f05-117">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="59f05-117">See Also</span></span>
- [<span data-ttu-id="59f05-118">Das Windows PowerShell ISE-Skriptobjektmodell</span><span class="sxs-lookup"><span data-stu-id="59f05-118">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
