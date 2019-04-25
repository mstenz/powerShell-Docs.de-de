---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Das PowerShellTabCollection-Objekt
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: d9088b26de35360b8258d3f15924b3010a986d15
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086612"
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="33b2e-103">Das PowerShellTabCollection-Objekt</span><span class="sxs-lookup"><span data-stu-id="33b2e-103">The PowerShellTabCollection Object</span></span>

<span data-ttu-id="33b2e-104">Das **PowerShellTab**-Sammlungsobjekt ist eine Sammlung von **PowerShellTab**-Objekten.</span><span class="sxs-lookup"><span data-stu-id="33b2e-104">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="33b2e-105">Jedes **PowerShellTab**-Objekt fungiert als eine separate Laufzeitumgebung.</span><span class="sxs-lookup"><span data-stu-id="33b2e-105">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="33b2e-106">Dies ist eine Instanz der Microsoft.PowerShell.Host.ISE.PowerShellTabs-Klasse.</span><span class="sxs-lookup"><span data-stu-id="33b2e-106">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="33b2e-107">Ein Beispiel ist das **$psISE.PowerShellTabs**-Objekt.</span><span class="sxs-lookup"><span data-stu-id="33b2e-107">An example is the **$psISE.PowerShellTabs** object.</span></span>

## <a name="methods"></a><span data-ttu-id="33b2e-108">Methoden</span><span class="sxs-lookup"><span data-stu-id="33b2e-108">Methods</span></span>

### <a name="add"></a><span data-ttu-id="33b2e-109">Add\(\)</span><span class="sxs-lookup"><span data-stu-id="33b2e-109">Add\(\)</span></span>

<span data-ttu-id="33b2e-110">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="33b2e-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="33b2e-111">Fügt eine neue PowerShell-Registerkarte zur Sammlung hinzu.</span><span class="sxs-lookup"><span data-stu-id="33b2e-111">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="33b2e-112">Die neu hinzugefügte Registerkarte wird zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="33b2e-112">It returns the newly added tab.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName = 'Brand New Tab'
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="33b2e-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="33b2e-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="33b2e-114">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="33b2e-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="33b2e-115">Entfernt die Registerkarte, die durch den **psTab**-Parameter angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="33b2e-115">Removes the tab that is specified by the **psTab** parameter.</span></span>

<span data-ttu-id="33b2e-116">**psTab** Die zu entfernende PowerShell-Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="33b2e-116">**psTab** The PowerShell tab to remove.</span></span>

```powershell
$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab.
$newTab.DisplayName = 'This tab will go away in 5 seconds'
sleep 5
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="33b2e-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="33b2e-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>

<span data-ttu-id="33b2e-118">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="33b2e-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span>

<span data-ttu-id="33b2e-119">Wählt die PowerShell-Registerkarte aus, die durch den **psTab**-Parameter angegeben wird, um diese als aktuell aktive PowerShell-Registerkarte festzulegen.</span><span class="sxs-lookup"><span data-stu-id="33b2e-119">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

<span data-ttu-id="33b2e-120">**psTab** Die auszuwählende PowerShell-Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="33b2e-120">**psTab** The PowerShell tab to select.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="33b2e-121">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="33b2e-121">See Also</span></span>

- [<span data-ttu-id="33b2e-122">Das PowerShellTab-Objekt</span><span class="sxs-lookup"><span data-stu-id="33b2e-122">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md)
- [<span data-ttu-id="33b2e-123">Zweck des Windows PowerShell ISE-Skriptobjektmodells</span><span class="sxs-lookup"><span data-stu-id="33b2e-123">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [<span data-ttu-id="33b2e-124">Die ISE-Objektmodellhierarchie</span><span class="sxs-lookup"><span data-stu-id="33b2e-124">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md)