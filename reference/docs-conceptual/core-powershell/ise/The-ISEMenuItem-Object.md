---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Das ISEMenuItem-Objekt
ms.assetid: a16660bd-0aee-46fd-ac17-3f022165d089
ms.openlocfilehash: 556f88117c07100b1734c8ffd8956dce6efe6fb1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30950708"
---
# <a name="the-isemenuitem-object"></a>Das ISEMenuItem-Objekt

Ein **ISEMenuItem**-Objekt ist eine Instanz der Microsoft.PowerShell.Host.ISE.ISEMenuItem-Klasse. Alle Menüobjekte im Menü **Add-Ons** sind Instanzen der **Microsoft.PowerShell.Host.ISE.ISEMenuItem**-Klasse.

## <a name="properties"></a>Eigenschaften

### <a name="displayname"></a>DisplayName

In Windows PowerShell ISE 2.0 und höher unterstützt.

Die schreibgeschützte Eigenschaft, die den Anzeigenamen des Menüelements abruft.

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a>Aktion

In Windows PowerShell ISE 2.0 und höher unterstützt.

Die schreibgeschützte Eigenschaft, die den Skriptblock abruft. Sie ruft die Aktion auf, wenn Sie auf das Menüelement klicken.

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a>Abkürzung

In Windows PowerShell ISE 2.0 und höher unterstützt.

Die schreibgeschützte Eigenschaft, die die Windows-Eingabetastenkombination für das Menüelement abruft.

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a>Submenus

In Windows PowerShell ISE 2.0 und höher unterstützt.

Die schreibgeschützte Eigenschaft, die die [Liste der Untermenüs](The-ISEMenuItemCollection-Object.md) für das Menüelement abruft.

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a>Beispielskript

Um die Verwendung des Menüs „Add-Ons“ und seiner skriptfähigen Eigenschaften besser zu verstehen, betrachten Sie das folgende Beispielskript.

```powershell
# This is a scripting example that shows the use of the Add-ons menu.
# Clear the Add-ons menu if any entries currently exist
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()

# Add an Add-ons menu item with an shortcut and fast access key.
# Note the use of “_”  as opposed to the “&” for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add('_Process', {Get-Process}, 'Alt+P')
# Add a nested menu - a parent and a child submenu item.
$parentAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('Parent', $null, $null)
$parentAdded.SubMenus.Add('_Dir', {dir}, 'Alt+D')
```

## <a name="see-also"></a>Weitere Informationen

- [Das ISEMenuItemCollection-Objekt](The-ISEMenuItemCollection-Object.md)
- [Zweck des Windows PowerShell ISE-Skriptobjektmodells](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Die ISE-Objektmodellhierarchie](The-ISE-Object-Model-Hierarchy.md)