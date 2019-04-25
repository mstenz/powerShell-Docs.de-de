---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Das ISEAddOnToolCollection-Objekt
ms.assetid: 634eab89-0845-4016-974b-361b09bb8f7b
ms.openlocfilehash: ff4f19d1a85a592f2f4f09c62caa0971751bdff7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057391"
---
# <a name="the-iseaddontoolcollection-object"></a><span data-ttu-id="d859f-103">Das ISEAddOnToolCollection-Objekt</span><span class="sxs-lookup"><span data-stu-id="d859f-103">The ISEAddOnToolCollection Object</span></span>

<span data-ttu-id="d859f-104">Das **ISEAddOnToolCollection**-Objekt ist eine Sammlung von **ISEAddOnTool**-Objekten.</span><span class="sxs-lookup"><span data-stu-id="d859f-104">The **ISEAddOnToolCollection** object is a collection of **ISEAddOnTool** objects.</span></span> <span data-ttu-id="d859f-105">Ein Beispiel ist das **$psISE.CurrentPowerShellTab.VerticalAddOnTools**-Objekt.</span><span class="sxs-lookup"><span data-stu-id="d859f-105">An example is the **$psISE.CurrentPowerShellTab.VerticalAddOnTools** object.</span></span>

## <a name="methods"></a><span data-ttu-id="d859f-106">Methoden</span><span class="sxs-lookup"><span data-stu-id="d859f-106">Methods</span></span>

### <a name="add-name-controltype-isvisible-"></a><span data-ttu-id="d859f-107">Add\( Name, ControlType, \[IsVisible\] \)</span><span class="sxs-lookup"><span data-stu-id="d859f-107">Add\( Name, ControlType, \[IsVisible\] \)</span></span>

<span data-ttu-id="d859f-108">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="d859f-108">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="d859f-109">Fügt der Sammlung ein neues Add-On-Tool hinzu.</span><span class="sxs-lookup"><span data-stu-id="d859f-109">Adds a new add-on tool to the collection.</span></span> <span data-ttu-id="d859f-110">Das neu hinzugefügte Add-On-Tool wird zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="d859f-110">It returns the newly added add-on tool.</span></span> <span data-ttu-id="d859f-111">Vor dem Ausführen dieses Befehls müssen Sie das Add-On-Tool auf dem lokalen Computer installieren und die Assembly laden.</span><span class="sxs-lookup"><span data-stu-id="d859f-111">Before you run this command, you must install the add-on tool on the local computer and load the assembly.</span></span>

<span data-ttu-id="d859f-112">**Name** – Zeichenfolge – gibt den Anzeigenamen des Add-On-Tools an, das zu Windows PowerShell ISE hinzugefügt wird</span><span class="sxs-lookup"><span data-stu-id="d859f-112">**Name** - String Specifies the display name of the add-on tool that is added to Windows PowerShell ISE.</span></span>

<span data-ttu-id="d859f-113">**ControlType** – Typ – gibt das Steuerelement an, das hinzugefügt wird</span><span class="sxs-lookup"><span data-stu-id="d859f-113">**ControlType** -Type Specifies the control that is added.</span></span>

<span data-ttu-id="d859f-114">**\[IsVisible\]** – optionaler boolescher Wert – bei **$true** ist das Add-On-Tool sofort im zugehörigen Toolbereich sichtbar</span><span class="sxs-lookup"><span data-stu-id="d859f-114">**\[IsVisible\]** - optional Boolean If set to **$true**, the add-on tool is immediately visible in the associated tool pane.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="remove-item-"></a><span data-ttu-id="d859f-115">Remove\( Item \)</span><span class="sxs-lookup"><span data-stu-id="d859f-115">Remove\( Item \)</span></span>

<span data-ttu-id="d859f-116">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="d859f-116">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="d859f-117">Entfernt das angegebene Add-On-Tool aus der Sammlung.</span><span class="sxs-lookup"><span data-stu-id="d859f-117">Removes the specified add-on tool from the collection.</span></span>

<span data-ttu-id="d859f-118">**Item** – Microsoft.PowerShell.Host.ISE.ISEAddOnTool – gibt das Objekt an, das aus Windows PowerShell ISE entfernt werden soll</span><span class="sxs-lookup"><span data-stu-id="d859f-118">**Item** - Microsoft.PowerShell.Host.ISE.ISEAddOnTool Specifies the object to be removed from Windows PowerShell ISE.</span></span>

```powershell
# Load a DLL with an add-on and then add it to the ISE
[reflection.assembly]::LoadFile("c:\test\ISESimpleSolution\ISESimpleSolution.dll")
$psISE.CurrentPowerShellTab.VerticalAddOnTools.Add("Solutions", [ISESimpleSolution.Solution], $true)
```

### <a name="setselectedpowershelltab-pstab-"></a><span data-ttu-id="d859f-119">SetSelectedPowerShellTab\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="d859f-119">SetSelectedPowerShellTab\( psTab \)</span></span>

<span data-ttu-id="d859f-120">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="d859f-120">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="d859f-121">Wählt die PowerShell-Registerkarte aus, die vom **psTab**-Parameter angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="d859f-121">Selects the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="d859f-122">**psTab** – Microsoft.PowerShell.Host.ISE.PowerShellTab – die auszuwählende PowerShell-Registerkarte</span><span class="sxs-lookup"><span data-stu-id="d859f-122">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to select.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
# Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="remove-pstab-"></a><span data-ttu-id="d859f-123">Remove\( psTab \)</span><span class="sxs-lookup"><span data-stu-id="d859f-123">Remove\( psTab \)</span></span>

<span data-ttu-id="d859f-124">In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.</span><span class="sxs-lookup"><span data-stu-id="d859f-124">Supported in Windows PowerShell ISE 3.0 and later, and not present in earlier versions.</span></span>

<span data-ttu-id="d859f-125">Entfernt die PowerShell Registerkarte, die vom **psTab**-Parameter angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="d859f-125">Removes the PowerShell tab that the **psTab** parameter specifies.</span></span>

<span data-ttu-id="d859f-126">**psTab** – Microsoft.PowerShell.Host.ISE.PowerShellTab – die zu entfernende PowerShell-Registerkarte</span><span class="sxs-lookup"><span data-stu-id="d859f-126">**psTab** - Microsoft.PowerShell.Host.ISE.PowerShellTab The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

## <a name="see-also"></a><span data-ttu-id="d859f-127">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d859f-127">See Also</span></span>

- [<span data-ttu-id="d859f-128">Das PowerShellTab-Objekt</span><span class="sxs-lookup"><span data-stu-id="d859f-128">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="d859f-129">Zweck des Windows PowerShell ISE-Skriptobjektmodells</span><span class="sxs-lookup"><span data-stu-id="d859f-129">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="d859f-130">Die ISE-Objektmodellhierarchie</span><span class="sxs-lookup"><span data-stu-id="d859f-130">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)