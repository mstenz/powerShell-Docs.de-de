---
ms.date: 2017-06-05T00:00:00.000Z
keywords: powershell,cmdlet
title: Das ISESnippet-Objekt
ms.assetid: 98bc8113-c3cd-4201-bdb9-9d9bdb7e266c
ms.openlocfilehash: 5cc49cd504a1343a5737f78eb886bb41591d087d
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2017
---
# <a name="the-isesnippetobject"></a>Das ISESnippet-Objekt
  Ein **ISESnippet**-Objekt ist eine Instanz der Microsoft.PowerShell.Host.ISE.ISESnippet-Klasse. Die Member der **$psISE.CurrentPowerShellTab.Snippets**-Sammlung sind Beispiele für **ISESnippet**-Objekte. Die einfachste Möglichkeit zum Erstellen eines Codeausschnitts ist die Verwendung des [New-IseSnippet&#91;PSITPro5_ISE&#93;](https://technet.microsoft.com/en-us/library/0a6339a3-2683-4a8e-8929-90ad9a95c3e0)-Cmdlets.

## <a name="properties"></a>Eigenschaften

###  <a name="DisplayName"></a> Author
  In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten. 

 Die schreibgeschützte Eigenschaft, die den Namen des Autors des Codeausschnitts abruft.

```
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author

```

###  <a name="Action"></a> CodeFragment
  In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten. 

 Die schreibgeschützte Eigenschaft, die das im Editor einzufügende Codefragment abruft.

```
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment

```

###  <a name="Shortcut"></a> Shortcut
  In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten. 

 Die schreibgeschützte Eigenschaft, die die Windows-Tastenkombination für das Menüelement abruft.

```
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.SubMenus.Add("_Process",{get-process},"Alt+P")
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a>Weitere Informationen
- [Das ISESnippetCollection-Objekt](The-ISESnippetCollection-Object.md) 
- [Das Windows PowerShell ISE-Skriptobjektmodell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md) 
- [Referenz zum Windows PowerShell ISE-Objektmodell](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [Die ISE-Objektmodellhierarchie](The-ISE-Object-Model-Hierarchy.md)

  
