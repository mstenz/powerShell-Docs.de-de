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
---
# <a name="the-isemenuitem-object"></a><span data-ttu-id="c2282-103">Das ISEMenuItem-Objekt</span><span class="sxs-lookup"><span data-stu-id="c2282-103">The ISEMenuItem Object</span></span>

<span data-ttu-id="c2282-104">Ein **ISEMenuItem**-Objekt ist eine Instanz der Microsoft.PowerShell.Host.ISE.ISEMenuItem-Klasse.</span><span class="sxs-lookup"><span data-stu-id="c2282-104">An **ISEMenuItem** object is an instance of the Microsoft.PowerShell.Host.ISE.ISEMenuItem class.</span></span> <span data-ttu-id="c2282-105">Alle Menüobjekte im Menü **Add-Ons** sind Instanzen der **Microsoft.PowerShell.Host.ISE.ISEMenuItem**-Klasse.</span><span class="sxs-lookup"><span data-stu-id="c2282-105">All menu objects on the **Add-ons** menu are instances of the **Microsoft.PowerShell.Host.ISE.ISEMenuItem** class.</span></span>

## <a name="properties"></a><span data-ttu-id="c2282-106">Eigenschaften</span><span class="sxs-lookup"><span data-stu-id="c2282-106">Properties</span></span>

### <a name="displayname"></a><span data-ttu-id="c2282-107">DisplayName</span><span class="sxs-lookup"><span data-stu-id="c2282-107">DisplayName</span></span>

<span data-ttu-id="c2282-108">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c2282-108">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c2282-109">Die schreibgeschützte Eigenschaft, die den Anzeigenamen des Menüelements abruft.</span><span class="sxs-lookup"><span data-stu-id="c2282-109">The read-only property that gets the display name of the menu item.</span></span>

```powershell
# Get the display name of the Add-ons menu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.DisplayName
```

### <a name="action"></a><span data-ttu-id="c2282-110">Aktion</span><span class="sxs-lookup"><span data-stu-id="c2282-110">Action</span></span>

<span data-ttu-id="c2282-111">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c2282-111">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c2282-112">Die schreibgeschützte Eigenschaft, die den Skriptblock abruft.</span><span class="sxs-lookup"><span data-stu-id="c2282-112">The read-only property that gets the block of script.</span></span> <span data-ttu-id="c2282-113">Sie ruft die Aktion auf, wenn Sie auf das Menüelement klicken.</span><span class="sxs-lookup"><span data-stu-id="c2282-113">It invokes the action when you click the menu item.</span></span>

```powershell
# Get the action associated with the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action

# Invoke the script associated with the first submenu item
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Action.Invoke()
```

### <a name="shortcut"></a><span data-ttu-id="c2282-114">Abkürzung</span><span class="sxs-lookup"><span data-stu-id="c2282-114">Shortcut</span></span>

<span data-ttu-id="c2282-115">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c2282-115">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c2282-116">Die schreibgeschützte Eigenschaft, die die Windows-Eingabetastenkombination für das Menüelement abruft.</span><span class="sxs-lookup"><span data-stu-id="c2282-116">The read-only property that gets the Windows input keyboard shortcut for the menu item.</span></span>

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

### <a name="submenus"></a><span data-ttu-id="c2282-117">Submenus</span><span class="sxs-lookup"><span data-stu-id="c2282-117">Submenus</span></span>

<span data-ttu-id="c2282-118">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c2282-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="c2282-119">Die schreibgeschützte Eigenschaft, die die [Liste der Untermenüs](The-ISEMenuItemCollection-Object.md) für das Menüelement abruft.</span><span class="sxs-lookup"><span data-stu-id="c2282-119">The read-only property that gets the [list of submenus](The-ISEMenuItemCollection-Object.md) of the menu item.</span></span>

```powershell
# List the submenus of the Add-ons menu
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus
```

## <a name="scripting-example"></a><span data-ttu-id="c2282-120">Beispielskript</span><span class="sxs-lookup"><span data-stu-id="c2282-120">Scripting example</span></span>

<span data-ttu-id="c2282-121">Um die Verwendung des Menüs „Add-Ons“ und seiner skriptfähigen Eigenschaften besser zu verstehen, betrachten Sie das folgende Beispielskript.</span><span class="sxs-lookup"><span data-stu-id="c2282-121">To better understand the use of the Add-ons menu and its scriptable properties, read through the following scripting example.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c2282-122">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="c2282-122">See Also</span></span>

- [<span data-ttu-id="c2282-123">Das ISEMenuItemCollection-Objekt</span><span class="sxs-lookup"><span data-stu-id="c2282-123">The ISEMenuItemCollection Object</span></span>](The-ISEMenuItemCollection-Object.md)
- [<span data-ttu-id="c2282-124">Zweck des Windows PowerShell ISE-Skriptobjektmodells</span><span class="sxs-lookup"><span data-stu-id="c2282-124">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="c2282-125">Die ISE-Objektmodellhierarchie</span><span class="sxs-lookup"><span data-stu-id="c2282-125">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)