---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Das ISEMenuItemCollection-Objekt
ms.openlocfilehash: b3795af1a6ed61ed6e371e5fc20cc4e95f643fd4
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030542"
---
# <a name="the-isemenuitemcollection-object"></a><span data-ttu-id="bb9d0-103">Das ISEMenuItemCollection-Objekt</span><span class="sxs-lookup"><span data-stu-id="bb9d0-103">The ISEMenuItemCollection Object</span></span>

<span data-ttu-id="bb9d0-104">Ein **ISEMenuItemCollection**-Objekt ist eine Sammlung von **ISEMenuItem**-Objekten.</span><span class="sxs-lookup"><span data-stu-id="bb9d0-104">An **ISEMenuItemCollection** object is a collection of **ISEMenuItem** objects.</span></span> <span data-ttu-id="bb9d0-105">Es ist eine Instanz der Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection-Klasse.</span><span class="sxs-lookup"><span data-stu-id="bb9d0-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection class.</span></span> <span data-ttu-id="bb9d0-106">Ein Beispiel ist das **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus**-Objekt, das verwendet wird, um das Menü **Add-On** in Windows PowerShell® Integrated Scripting Environment (ISE) anzupassen.</span><span class="sxs-lookup"><span data-stu-id="bb9d0-106">An example is the **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** object that is used to customize the **Add-On** menu in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span>

## <a name="method"></a><span data-ttu-id="bb9d0-107">Methode</span><span class="sxs-lookup"><span data-stu-id="bb9d0-107">Method</span></span>

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a><span data-ttu-id="bb9d0-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span><span class="sxs-lookup"><span data-stu-id="bb9d0-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span></span>

<span data-ttu-id="bb9d0-109">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="bb9d0-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bb9d0-110">Fügt der Sammlung ein Menüelement hinzu.</span><span class="sxs-lookup"><span data-stu-id="bb9d0-110">Adds a menu item to the collection.</span></span>

<span data-ttu-id="bb9d0-111">**DisplayName** Der Anzeigename des hinzuzufügenden Menüs.</span><span class="sxs-lookup"><span data-stu-id="bb9d0-111">**DisplayName** The display name of the menu to be added.</span></span>

<span data-ttu-id="bb9d0-112">**Action** Das **System.Management.Automation.ScriptBlock**-Objekt, das die diesem Menüelement zugeordnete Aktion angibt.</span><span class="sxs-lookup"><span data-stu-id="bb9d0-112">**Action** The **System.Management.Automation.ScriptBlock** object that specifies the action that is associated with this menu item.</span></span>

<span data-ttu-id="bb9d0-113">**Shortcut** Die Tastenkombination für diese Aktion.</span><span class="sxs-lookup"><span data-stu-id="bb9d0-113">**Shortcut** The keyboard shortcut for the action.</span></span>

<span data-ttu-id="bb9d0-114">**Returns** Das ISEMenuItem-Objekt, das soeben hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="bb9d0-114">**Returns** The ISEMenuItem object that was just added.</span></span>

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a><span data-ttu-id="bb9d0-115">Clear\(\)</span><span class="sxs-lookup"><span data-stu-id="bb9d0-115">Clear\(\)</span></span>

<span data-ttu-id="bb9d0-116">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="bb9d0-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="bb9d0-117">Entfernt alle Untermenüs des Menüelements.</span><span class="sxs-lookup"><span data-stu-id="bb9d0-117">Removes all submenus from the menu item.</span></span>

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a><span data-ttu-id="bb9d0-118">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="bb9d0-118">See Also</span></span>

- [<span data-ttu-id="bb9d0-119">Das ISEMenuItem-Objekt</span><span class="sxs-lookup"><span data-stu-id="bb9d0-119">The ISEMenuItem Object</span></span>](The-ISEMenuItem-Object.md)
- [<span data-ttu-id="bb9d0-120">Zweck des Windows PowerShell ISE-Skriptobjektmodells</span><span class="sxs-lookup"><span data-stu-id="bb9d0-120">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="bb9d0-121">Die ISE-Objektmodellhierarchie</span><span class="sxs-lookup"><span data-stu-id="bb9d0-121">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
