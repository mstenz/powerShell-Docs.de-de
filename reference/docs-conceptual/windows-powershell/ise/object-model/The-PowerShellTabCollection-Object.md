---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Das PowerShellTabCollection-Objekt
ms.openlocfilehash: 0aad885afd3ba3ae3b00f5c11d2c62a9ff303798
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83808566"
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="64b6d-103">Das PowerShellTabCollection-Objekt</span><span class="sxs-lookup"><span data-stu-id="64b6d-103">The PowerShellTabCollection Object</span></span>

<span data-ttu-id="64b6d-104">Das **PowerShellTab**-Sammlungsobjekt ist eine Sammlung von **PowerShellTab**-Objekten.</span><span class="sxs-lookup"><span data-stu-id="64b6d-104">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="64b6d-105">Jedes **PowerShellTab**-Objekt fungiert als eine separate Laufzeitumgebung.</span><span class="sxs-lookup"><span data-stu-id="64b6d-105">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="64b6d-106">Dies ist eine Instanz der Microsoft.PowerShell.Host.ISE.PowerShellTabs-Klasse.</span><span class="sxs-lookup"><span data-stu-id="64b6d-106">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="64b6d-107">Ein Beispiel ist das `$psISE.PowerShellTabs`-Objekt.</span><span class="sxs-lookup"><span data-stu-id="64b6d-107">An example is the `$psISE.PowerShellTabs` object.</span></span>

## <a name="methods"></a><span data-ttu-id="64b6d-108">Methoden</span><span class="sxs-lookup"><span data-stu-id="64b6d-108">Methods</span></span>

### <a name="add"></a><span data-ttu-id="64b6d-109">Add\(\)</span><span class="sxs-lookup"><span data-stu-id="64b6d-109">Add\(\)</span></span>

<span data-ttu-id="64b6d-110">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="64b6d-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="64b6d-111">Fügt eine neue PowerShell-Registerkarte zur Sammlung hinzu.</span><span class="sxs-lookup"><span data-stu-id="64b6d-111">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="64b6d-112">Die neu hinzugefügte Registerkarte wird zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="64b6d-112">It returns the newly added tab.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="64b6d-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="64b6d-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="64b6d-114">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="64b6d-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="64b6d-115">Entfernt die Registerkarte, die durch den **psTab**-Parameter angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="64b6d-115">Removes the tab that is specified by the **psTab** parameter.</span></span>

<span data-ttu-id="64b6d-116">**psTab** Die zu entfernende PowerShell-Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="64b6d-116">**psTab** The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="64b6d-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="64b6d-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="64b6d-118">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="64b6d-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="64b6d-119">Wählt die PowerShell-Registerkarte aus, die durch den **psTab**-Parameter angegeben wird, um diese als aktuell aktive PowerShell-Registerkarte festzulegen.</span><span class="sxs-lookup"><span data-stu-id="64b6d-119">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

<span data-ttu-id="64b6d-120">**psTab** Die auszuwählende PowerShell-Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="64b6d-120">**psTab** The PowerShell tab to select.</span></span>

```powershell
# Save the current tab in a variable and rename it
$oldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName = 'Old Tab'
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab = $oldTab
```

## <a name="see-also"></a><span data-ttu-id="64b6d-121">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="64b6d-121">See Also</span></span>

- [<span data-ttu-id="64b6d-122">Das PowerShellTab-Objekt</span><span class="sxs-lookup"><span data-stu-id="64b6d-122">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="64b6d-123">Zweck des Windows PowerShell ISE-Skriptobjektmodells</span><span class="sxs-lookup"><span data-stu-id="64b6d-123">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="64b6d-124">Die ISE-Objektmodellhierarchie</span><span class="sxs-lookup"><span data-stu-id="64b6d-124">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)
