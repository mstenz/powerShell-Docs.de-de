---
ms.date: 08/25/2017
keywords: powershell,cmdlet
title: Das ObjectModelRoot-Objekt
ms.openlocfilehash: cd94e69de2e62f7ce9fac413e15458ae9986540e
ms.sourcegitcommit: 2aec310ad0c0b048400cb56f6fa64c1e554c812a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/23/2020
ms.locfileid: "83809566"
---
# <a name="the-objectmodelroot-object"></a>Das ObjectModelRoot-Objekt

Das `$psISE`-Objekt ist das Prinzipalstammobjekt in Windows PowerShell® Integrated Scripting Environment (ISE) und eine Instanz der Microsoft.PowerShell.Host.ISE.ObjectModelRoot-Klasse. Dieses Thema beschreibt die Eigenschaften des **ObjectModelRoot**-Objekts.

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

### <a name="options"></a>Tastatur

> In Windows PowerShell ISE 2.0 und höher unterstützt.

Die schreibgeschützte Eigenschaft, mit der die verschiedenen Optionen zum Ändern von Eigenschaften in Windows PowerShell ISE abgerufen werden.

### <a name="powershelltabs"></a>PowerShellTabs

> In Windows PowerShell ISE 2.0 und höher unterstützt.

Die schreibgeschützte Eigenschaft, die die Sammlung von in Windows PowerShell ISE geöffneten PowerShell-Registerkarten abruft. Standardmäßig enthält dieses Objekt eine PowerShell-Registerkarte. Allerdings können Sie mit Skripts oder Menüs in Windows PowerShell ISE weitere PowerShell-Registerkarten zu diesem Objekt hinzufügen.

## <a name="see-also"></a>Weitere Informationen

- [Zweck des Windows PowerShell ISE-Skriptobjektmodells](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Die ISE-Objektmodellhierarchie](The-ISE-Object-Model-Hierarchy.md)
