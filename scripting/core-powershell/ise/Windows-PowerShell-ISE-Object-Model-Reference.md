---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Referenz zum Windows PowerShell ISE-Objektmodell
ms.assetid: e1a9e7d1-0fd5-47de-8d9b-f1be1ed13b0c
ms.openlocfilehash: e5d4ae03158d9b5b0efd98db1272bc13872181ac
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2017
---
# <a name="windows-powershell-ise-object-model-reference"></a>Referenz zum Windows PowerShell ISE-Objektmodell
  
## <a name="object-model-reference"></a>Objektmodellreferenz
 Dieser Abschnitt enthält eine Referenz für die zugrunde liegenden Klassen, die die verschiedenen Objekte in Windows PowerShell® Integrated Scripting Environment (ISE) definieren. Informationen dazu, wie Sie die Objekte in der Hierarchie angeordnet anzeigen, finden Sie unter [Die ISE-Objektmodellhierarchie](The-ISE-Object-Model-Hierarchy.md).

 [Das ISEAddOnTool-Objekt](The-ISEAddOnTool-Object.md)
 Beispiele: $psISE.CurrentVisibleHorizontalTool, $psISE.CurrentVisibleVerticalTool.

 [Das ISEAddOnTool-Objekt](The-ISEAddOnTool-Object.md)
  [Das ISEEditor-Objekt](The-ISEEditor-Object.md)
 Beispiele: $psISE.CurrentFile.Editor, $psISE.CurrentPowerShellTab.Output, $psISE.CurrentPowerShellTab.CommandPane.

 [Das ISEFile-Objekt](The-ISEFile-Object.md)
 Beispiele: $psISE.CurrentFile, $psISE.PowerShellTabs.Files\[0\].

 [Das ISEFileCollection-Objekt](The-ISEFileCollection-Object.md)
 Beispiele: $psISE.PowerShellTabs.Files.

 [Das ISEMenuItem-Objekt](The-ISEMenuItem-Object.md)
 Beispiele: $psISE.CurrentPowerShellTab.AddOnsMenu, $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus\[0\].

 [Das ISEMenuItemCollection-Objekt](The-ISEMenuItemCollection-Object.md)
 Beispiel: $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.

 [Das ISEOptions-Objekt](The-ISEOptions-Object.md)
 Beispiele: $psISE.Options, $psISE.Options.DefaultOptions.

 [Das ObjectModelRoot-Objekt](The-ObjectModelRoot-Object.md)
 Beispiel: Das $psISE-Stammobjekt.

 [Das PowerShellTab-Objekt](The-PowerShellTab-Object.md)
 Beispiele: $psISE.CurrentPowerShellTab, $psISE.PowerShellTabs\[0\].

 [Das PowerShellTabCollection-Objekt](The-PowerShellTabCollection-Object.md)
 Beispiel: $psISE.PowerShellTabs.

## <a name="see-also"></a>Weitere Informationen
- [Das Windows PowerShell ISE-Skriptobjektmodell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
