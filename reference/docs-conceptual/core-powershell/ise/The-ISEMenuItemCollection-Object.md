---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Das ISEMenuItemCollection-Objekt
ms.assetid: 0c0f5484-3320-408e-8534-5bd1c8e48512
ms.openlocfilehash: 7e5030416df394aaa9e9d3f63978e204a7faabf1
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
---
# <a name="the-isemenuitemcollection-object"></a><span data-ttu-id="15d4d-103">Das ISEMenuItemCollection-Objekt</span><span class="sxs-lookup"><span data-stu-id="15d4d-103">The ISEMenuItemCollection Object</span></span>

<span data-ttu-id="15d4d-104">Ein **ISEMenuItemCollection**-Objekt ist eine Sammlung von **ISEMenuItem**-Objekten.</span><span class="sxs-lookup"><span data-stu-id="15d4d-104">An **ISEMenuItemCollection** object is a collection of **ISEMenuItem** objects.</span></span> <span data-ttu-id="15d4d-105">Es ist eine Instanz der Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection-Klasse.</span><span class="sxs-lookup"><span data-stu-id="15d4d-105">It is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItemCollection class.</span></span> <span data-ttu-id="15d4d-106">Ein Beispiel ist das **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus**-Objekt, das verwendet wird, um das Menü **Add-On** in Windows PowerShell® Integrated Scripting Environment (ISE) anzupassen.</span><span class="sxs-lookup"><span data-stu-id="15d4d-106">An example is the **$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus** object that is used to customize the **Add-On** menu in Windows PowerShell® Integrated Scripting Environment (ISE).</span></span>

## <a name="method"></a><span data-ttu-id="15d4d-107">Methode</span><span class="sxs-lookup"><span data-stu-id="15d4d-107">Method</span></span>

### <a name="addstring-displayname-systemmanagementautomationscriptblock-action-systemwindowsinputkeygesture-shortcut-"></a><span data-ttu-id="15d4d-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span><span class="sxs-lookup"><span data-stu-id="15d4d-108">Add\(string DisplayName, System.Management.Automation.ScriptBlock Action, System.Windows.Input.KeyGesture Shortcut \)</span></span>

<span data-ttu-id="15d4d-109">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="15d4d-109">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="15d4d-110">Fügt der Sammlung ein Menüelement hinzu.</span><span class="sxs-lookup"><span data-stu-id="15d4d-110">Adds a menu item to the collection.</span></span>

<span data-ttu-id="15d4d-111">**DisplayName** Der Anzeigename des hinzuzufügenden Menüs.</span><span class="sxs-lookup"><span data-stu-id="15d4d-111">**DisplayName** The display name of the menu to be added.</span></span>

<span data-ttu-id="15d4d-112">**Action** Das **System.Management.Automation.ScriptBlock**-Objekt, das die diesem Menüelement zugeordnete Aktion angibt.</span><span class="sxs-lookup"><span data-stu-id="15d4d-112">**Action** The **System.Management.Automation.ScriptBlock** object that specifies the action that is associated with this menu item.</span></span>

<span data-ttu-id="15d4d-113">**Shortcut** Die Tastenkombination für diese Aktion.</span><span class="sxs-lookup"><span data-stu-id="15d4d-113">**Shortcut** The keyboard shortcut for the action.</span></span>

<span data-ttu-id="15d4d-114">**Returns** Das ISEMenuItem-Objekt, das soeben hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="15d4d-114">**Returns** The ISEMenuItem object that was just added.</span></span>

```powershell
# Create an Add-ons menu with an fast access key and a shortcut.
# Note the use of "_"  as opposed to the "&" for mapping to the fast access key letter for the menu item.
$menuAdded = $psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
```

### <a name="clear"></a><span data-ttu-id="15d4d-115">Clear\(\)</span><span class="sxs-lookup"><span data-stu-id="15d4d-115">Clear\(\)</span></span>

<span data-ttu-id="15d4d-116">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="15d4d-116">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="15d4d-117">Entfernt alle Untermenüs des Menüelements.</span><span class="sxs-lookup"><span data-stu-id="15d4d-117">Removes all submenus from the menu item.</span></span>

```powershell
# Remove all custom submenu items from the AddOns menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
```

## <a name="see-also"></a><span data-ttu-id="15d4d-118">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="15d4d-118">See Also</span></span>

- [<span data-ttu-id="15d4d-119">Das ISEMenuItem-Objekt</span><span class="sxs-lookup"><span data-stu-id="15d4d-119">The ISEMenuItem Object</span></span>](The-ISEMenuItem-Object.md)
- [<span data-ttu-id="15d4d-120">Zweck des Windows PowerShell ISE-Skriptobjektmodells</span><span class="sxs-lookup"><span data-stu-id="15d4d-120">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="15d4d-121">Die ISE-Objektmodellhierarchie</span><span class="sxs-lookup"><span data-stu-id="15d4d-121">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)