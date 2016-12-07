---
title: Referenz zum Windows PowerShell ISE-Objektmodell
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: e1a9e7d1-0fd5-47de-8d9b-f1be1ed13b0c
ms.openlocfilehash: 44d5f142c6d2c68c1a70b3a1017a8e6e57a58abe
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
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

  
