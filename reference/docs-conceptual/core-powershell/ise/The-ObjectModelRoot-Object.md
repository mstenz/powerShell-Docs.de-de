---
ms.date: 2017-08-25
keywords: powershell,cmdlet
title: Das ObjectModelRoot-Objekt
ms.openlocfilehash: eb3424ff147c35364fa08543d59ebd30f6d2d857
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2017
---
# <a name="the-objectmodelroot-object"></a>Das ObjectModelRoot-Objekt

Das **$psISE**-Objekt, das das Prinzipalstammobjekt in Windows PowerShell® Integrated Scripting Environment (ISE) ist, ist eine Instanz der Microsoft.PowerShell.Host.ISE.ObjectModelRoot-Klasse.
Dieses Thema beschreibt die Eigenschaften des **ObjectModelRoot**-Objekts.

## <a name="properties"></a>Eigenschaften

### <a name="currentfile"></a>CurrentFile

> In Windows PowerShell ISE 2.0 und höher unterstützt. 

Die schreibgeschützte Eigenschaft, die die diesem Hostobjekt, das gegenwärtig den Fokus besitzt, zugeordnete Datei abruft.

### <a name="currentpowershelltab"></a>CurrentPowerShellTab

> In Windows PowerShell ISE 2.0 und höher unterstützt.

Die schreibgeschützte Eigenschaft, die die PowerShell-Registerkarte abruft, die zurzeit den Fokus besitzt.

### <a name="currentvisiblehorizontaltool"></a>CurrentVisibleHorizontalTool

> In Windows PowerShell ISE 2.0 und höher unterstützt.

Die schreibgeschützte Eigenschaft, die das derzeit sichtbare Windows PowerShell ISE-Add-On-Tool abruft, das sich im horizontalen Toolbereich unten im Editor befindet.

### <a name="currentvisibleverticaltool"></a>CurrentVisibleVerticalTool

> In Windows PowerShell ISE 2.0 und höher unterstützt. 

Die schreibgeschützte Eigenschaft, die das derzeit sichtbare Windows PowerShell ISE-Add-On-Tool abruft, das sich im vertikalen Toolbereich rechts im Editor befindet.

### <a name="options"></a>Optionen

> In Windows PowerShell ISE 2.0 und höher unterstützt. 

Die schreibgeschützte Eigenschaft, mit der die verschiedenen Optionen zum Ändern von Eigenschaften in Windows PowerShell ISE abgerufen werden.

### <a name="powershelltabs"></a>PowerShellTabs

> In Windows PowerShell ISE 2.0 und höher unterstützt. 

Die schreibgeschützte Eigenschaft, die die Sammlung von in Windows PowerShell ISE geöffneten PowerShell-Registerkarten abruft. Standardmäßig enthält dieses Objekt eine PowerShell-Registerkarte. Allerdings können Sie mit Skripts oder Menüs in Windows PowerShell ISE weitere PowerShell-Registerkarten zu diesem Objekt hinzufügen.

## <a name="see-also"></a>Weitere Informationen

- [Das Windows PowerShell ISE-Skriptobjektmodell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Referenz zum Windows PowerShell ISE-Objektmodell](Windows-PowerShell-ISE-Object-Model-Reference.md)
- [Die ISE-Objektmodellhierarchie](The-ISE-Object-Model-Hierarchy.md)
