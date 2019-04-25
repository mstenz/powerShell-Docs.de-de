---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Das ISEMenuItemCollection-Objekt
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 7e5030416df394aaa9e9d3f63978e204a7faabf1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086696"
---
# <a name="the-isemenuitemcollection-object"></a>Das ISEMenuItemCollection-Objekt

Ein **ISEMenuItemCollection**-Objekt ist eine Sammlung von **ISEMenuItem**-Objekten. Es ist eine Instanz der Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection-Klasse. Ein Beispiel ist das **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus**-Objekt, das verwendet wird, um das Menü **Add-On** in Windows PowerShell® Integrated Scripting Environment (ISE) anzupassen.

## <a name="method"></a>Methode

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a>Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)

In Windows PowerShell ISE 2.0 und höher unterstützt.

Fügt der Sammlung ein Menüelement hinzu.

**DisplayName** Der Anzeigename des hinzuzufügenden Menüs.

**Action** Das **System.Management.Automation.ScriptBlock**-Objekt, das die diesem Menüelement zugeordnete Aktion angibt.

**Shortcut** Die Tastenkombination für diese Aktion.

**Returns** Das ISEMenuItem-Objekt, das soeben hinzugefügt wurde.

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a>Clear\(\)

In Windows PowerShell ISE 2.0 und höher unterstützt.

Entfernt alle Untermenüs des Menüelements.

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a>Weitere Informationen

- [Das ISEMenuItem-Objekt](The-ISEMenuItem-Object.md)
- [Zweck des Windows PowerShell ISE-Skriptobjektmodells](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Die ISE-Objektmodellhierarchie](The-ISE-Object-Model-Hierarchy.md)