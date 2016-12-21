---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: Das ISEMenuItemCollection-Objekt
ms.technology: powershell
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 45e9123df5f22f37d2a76e49db6df5aa98824e1c
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="the-isemenuitemcollection-object"></a>Das ISEMenuItemCollection-Objekt
  Ein **ISEMenuItemCollection**-Objekt ist eine Sammlung von **ISEMenuItem**-Objekten. Es ist eine Instanz der Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection-Klasse. Ein Beispiel ist das **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus**-Objekt, das verwendet wird, um das Menü **Add-On** in Windows PowerShell® Integrated Scripting Environment (ISE) anzupassen.

## <a name="method"></a>Methode

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Fügt der Sammlung ein Menüelement hinzu.

 **DisplayName**
 Der Anzeigename des hinzuzufügenden Menüs.

 **Action**
 Das **System.Management.Automation.ScriptBlock**-Objekt, das die diesem Menüelement zugeordnete Aktion angibt.

 **Shortcut**
 Die Tastenkombination für diese Aktion.

 **Returns**
 Das ISEMenuItem-Objekt, das soeben hinzugefügt wurde.

```
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
```

### <a name="clear"></a>Clear\(\)
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Entfernt alle Untermenüs des Menüelements.

```
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

```

## <a name="see-also"></a>Weitere Informationen
- [Das ISEMenuItem-Objekt](The-ISEMenuItem-Object.md) 
- [Das Windows PowerShell ISE-Skriptobjektmodell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Referenz zum Windows PowerShell ISE-Objektmodell](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [Die ISE-Objektmodellhierarchie](The-ISE-Object-Model-Hierarchy.md)

  
