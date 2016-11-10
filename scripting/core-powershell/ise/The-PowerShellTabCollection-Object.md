---
title: Das PowerShellTabCollection-Objekt
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 81f4bf4a-83bf-415e-8378-1703792fbb58
translationtype: Human Translation
ms.sourcegitcommit: 6c666e2e23cb74818e37293410dafc9033057733
ms.openlocfilehash: 948c7347a4794a1d0cb8369a34e2d5c21ad78241

---

# Das PowerShellTabCollection-Objekt
  Das **PowerShellTab**-Sammlungsobjekt ist eine Sammlung von **PowerShellTab**-Objekten. Jedes **PowerShellTab**-Objekt fungiert als eine separate Laufzeitumgebung. Dies ist eine Instanz der Microsoft.PowerShell.Host.ISE.PowerShellTabs-Klasse. Ein Beispiel ist das **$psISE.PowerShellTabs**-Objekt.

## Methoden

### Hinzufügen\(\)
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Fügt eine neue PowerShell-Registerkarte zur Sammlung hinzu. Die neu hinzugefügte Registerkarte wird zurückgegeben.

```
$NewTab=$psISE.PowerShellTabs.Add()
$newTab.DisplayName="Brand New Tab"
```

### Remove\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Entfernt die Registerkarte, die durch den **psTab**-Parameter angegeben wird.

 **psTab**
 Die zu entfernende PowerShell-Registerkarte.

```

$newTab = $psISE.PowerShellTabs.Add()
Change the DisplayName of the new PowerShell tab. 
$newTab.DisplayName="This tab will go away in 5 seconds" 
sleep 5 
$psISE.PowerShellTabs.Remove($newTab)
```

### SetSelectedPowerShellTab\(Microsoft.PowerShell.Host.ISE.PowerShellTab psTab\)
  In Windows PowerShell ISE 2.0 und höher unterstützt. 

 Wählt die PowerShell-Registerkarte aus, die durch den **psTab**-Parameter angegeben wird, um diese als aktuell aktive PowerShell-Registerkarte festzulegen.

 **psTab**
 Die auszuwählende PowerShell-Registerkarte.

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

## Weitere Informationen
- [Das PowerShellTab-Objekt](The-PowerShellTab-Object.md) 
- [Das Windows PowerShell ISE-Skriptobjektmodell](../ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Referenz zum Windows PowerShell ISE-Objektmodell](../ise/Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [Die ISE-Objektmodellhierarchie](../ise/The-ISE-Object-Model-Hierarchy.md)

  



<!--HONumber=Oct16_HO3-->


