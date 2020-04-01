---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Das ISESnippet-Objekt
ms.openlocfilehash: f810e6b26f0ded04be15bdc37f336d7890e29dad
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500922"
---
# <a name="the-isesnippetobject"></a>Das ISESnippet-Objekt

Ein **ISESnippet**-Objekt ist eine Instanz der Microsoft.PowerShell.Host.ISE.ISESnippet-Klasse. Die Member der `$psISE.CurrentPowerShellTab.Snippets`-Sammlung sind Beispiele für **ISESnippet**-Objekte. Die einfachste Möglichkeit zum Erstellen eines Codeausschnitts ist die Verwendung des [New-IseSnippet](/powershell/module/ISE/New-IseSnippet)-Cmdlets.

## <a name="properties"></a>Eigenschaften

### <a name="author"></a>Autor

In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.

Die schreibgeschützte Eigenschaft, die den Namen des Autors des Codeausschnitts abruft.

```powershell
# Get the author of the first snippet item
$psISE.CurrentPowerShellTab.Snippets.Item(0).Author
```

### <a name="codefragment"></a>CodeFragment

In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.

Die schreibgeschützte Eigenschaft, die das im Editor einzufügende Codefragment abruft.

```powershell
# Get the code fragment associated with the first snippet item.
$psISE.CurrentPowerShellTab.Snippets.Item(0).CodeFragment
```

### <a name="shortcut"></a>Tastenkombination

In Windows PowerShell ISE 3.0 und höher unterstützt, in früheren Versionen nicht enthalten.

Die schreibgeschützte Eigenschaft, die die Windows-Tastenkombination für das Menüelement abruft.

```powershell
# Get the shortcut for the first submenu item.
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Clear()
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus.Add('_Process', {Get-Process}, 'Alt+P')
$psISE.CurrentPowerShellTab.AddOnsMenu.Submenus[0].Shortcut
```

## <a name="see-also"></a>Weitere Informationen

- [Das ISESnippetCollection-Objekt](The-ISESnippetCollection-Object.md)
- [Zweck des Windows PowerShell ISE-Skriptobjektmodells](purpose-of-the-windows-powershell-ise-scripting-object-model.md)
- [Die ISE-Objektmodellhierarchie](The-ISE-Object-Model-Hierarchy.md)
