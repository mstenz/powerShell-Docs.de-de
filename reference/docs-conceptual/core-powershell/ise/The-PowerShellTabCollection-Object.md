---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Das PowerShellTabCollection-Objekt
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
ms.openlocfilehash: dcdc16ae126453b6ade64917ac4950cc05e5f8ad
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/08/2017
---
# <a name="the-powershelltabcollection-object"></a><span data-ttu-id="4f272-103">Das PowerShellTabCollection-Objekt</span><span class="sxs-lookup"><span data-stu-id="4f272-103">The PowerShellTabCollection Object</span></span>
  <span data-ttu-id="4f272-104">Das **PowerShellTab**-Sammlungsobjekt ist eine Sammlung von **PowerShellTab**-Objekten.</span><span class="sxs-lookup"><span data-stu-id="4f272-104">The **PowerShellTab** collection object is a collection of **PowerShellTab** objects.</span></span> <span data-ttu-id="4f272-105">Jedes **PowerShellTab**-Objekt fungiert als eine separate Laufzeitumgebung.</span><span class="sxs-lookup"><span data-stu-id="4f272-105">Each **PowerShellTab** object functions as a separate runtime environment.</span></span> <span data-ttu-id="4f272-106">Dies ist eine Instanz der Microsoft.PowerShell.Host.ISE.PowerShellTabs-Klasse.</span><span class="sxs-lookup"><span data-stu-id="4f272-106">It is an instance of Microsoft.PowerShell.Host.ISE.PowerShellTabs class.</span></span> <span data-ttu-id="4f272-107">Ein Beispiel ist das **$psISE.PowerShellTabs**-Objekt.</span><span class="sxs-lookup"><span data-stu-id="4f272-107">An example is the **$psISE.PowerShellTabs** object.</span></span>

## <a name="methods"></a><span data-ttu-id="4f272-108">Methoden</span><span class="sxs-lookup"><span data-stu-id="4f272-108">Methods</span></span>

### <a name="add"></a><span data-ttu-id="4f272-109">Add\(\)</span><span class="sxs-lookup"><span data-stu-id="4f272-109">Add\(\)</span></span>
  <span data-ttu-id="4f272-110">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="4f272-110">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="4f272-111">Fügt eine neue PowerShell-Registerkarte zur Sammlung hinzu.</span><span class="sxs-lookup"><span data-stu-id="4f272-111">Adds a new PowerShell tab to the collection.</span></span> <span data-ttu-id="4f272-112">Die neu hinzugefügte Registerkarte wird zurückgegeben.</span><span class="sxs-lookup"><span data-stu-id="4f272-112">It returns the newly added tab.</span></span>

```
$NewTab=$psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab"
```

### <a name="removemicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="4f272-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="4f272-113">Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>
  <span data-ttu-id="4f272-114">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="4f272-114">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="4f272-115">Entfernt die Registerkarte, die durch den **psTab**-Parameter angegeben wird.</span><span class="sxs-lookup"><span data-stu-id="4f272-115">Removes the tab that is specified by the **psTab** parameter.</span></span>

 <span data-ttu-id="4f272-116">**psTab**
 Die zu entfernende PowerShell-Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="4f272-116">**psTab**
 The PowerShell tab to remove.</span></span>

```

$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

### <a name="setselectedpowershelltabmicrosoftpowershellhostisepowershelltab-pstab"></a><span data-ttu-id="4f272-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span><span class="sxs-lookup"><span data-stu-id="4f272-117">SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)</span></span>
  <span data-ttu-id="4f272-118">In Windows PowerShell ISE 2.0 und höher unterstützt.</span><span class="sxs-lookup"><span data-stu-id="4f272-118">Supported in Windows PowerShell ISE 2.0 and later.</span></span> 

 <span data-ttu-id="4f272-119">Wählt die PowerShell-Registerkarte aus, die durch den **psTab**-Parameter angegeben wird, um diese als aktuell aktive PowerShell-Registerkarte festzulegen.</span><span class="sxs-lookup"><span data-stu-id="4f272-119">Selects the PowerShell tab that is specified by the **psTab** parameter to make it the currently active PowerShell tab.</span></span>

 <span data-ttu-id="4f272-120">**psTab**
 Die auszuwählende PowerShell-Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="4f272-120">**psTab**
 The PowerShell tab to select.</span></span>

```
# Save the current tab in a variable and rename it
$OldTab = $psISE.CurrentPowerShellTab
$psISE.CurrentPowerShellTab.DisplayName="Old Tab"
# Create a new tab and give it a new display name
$newTab = $psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab" 
# Switch back to the original tab
$psISE.PowerShellTabs.SelectedPowerShellTab=$oldtab
```

## <a name="see-also"></a><span data-ttu-id="4f272-121">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="4f272-121">See Also</span></span>
- [<span data-ttu-id="4f272-122">Das PowerShellTab-Objekt</span><span class="sxs-lookup"><span data-stu-id="4f272-122">The PowerShellTab Object</span></span>](The-PowerShellTab-Object.md) 
- [<span data-ttu-id="4f272-123">Das Windows PowerShell ISE-Skriptobjektmodell</span><span class="sxs-lookup"><span data-stu-id="4f272-123">The Windows PowerShell ISE Scripting Object Model</span></span>](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [<span data-ttu-id="4f272-124">Referenz zum Windows PowerShell ISE-Objektmodell</span><span class="sxs-lookup"><span data-stu-id="4f272-124">Windows PowerShell ISE Object Model Reference</span></span>](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="4f272-125">Die ISE-Objektmodellhierarchie</span><span class="sxs-lookup"><span data-stu-id="4f272-125">The ISE Object Model Hierarchy</span></span>](../ise/The-ISE-Object-Model-Hierarchy.md)

  
