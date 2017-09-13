---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Die ISE-Objektmodellhierarchie
ms.openlocfilehash: 2df6d40f39dbe14bd3f46a6400cde4a6e91052ef
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/08/2017
---
# <a name="the-ise-object-model-hierarchy"></a>Die ISE-Objektmodellhierarchie
In diesem Thema wird die Hierarchie der Objekte beschrieben, die Teil von Windows PowerShell Integrated Scripting Environment (ISE) sind. Windows PowerShell ISE ist in Windows PowerShell 3.0 und in Windows PowerShell 4.0 enthalten. Klicken Sie auf ein Objekt, um die Dokumentation für die Klasse aufzurufen, die das Objekt definiert.

## <a name="psise-object"></a>$psISE-Objekt

Das **$psISE**-Objekt ist das [Stammobjekt](The-ObjectModelRoot-Object.md) der Windows PowerShell ISE-Objekthierarchie.
Es befindet sich auf der obersten Ebene und macht die folgenden Objekte für Skripts verfügbar:

## <a name="psisecurrentfilethe-isefile-objectmd"></a>[$psISE.CurrentFile](The-ISEFile-Object.md)

Das **$psISE.CurrentFile**-Objekt ist eine Instanz der [ISEFile](The-ISEFile-Object.md)-Klasse.

## <a name="psisecurrentpowershelltabthe-powershelltab-objectmd"></a>[$psISE.CurrentPowerShellTab](The-PowerShellTab-Object.md)

Das **$psISE.CurrentPowerShellTab**-Objekt ist eine Instanz der [PowerShellTab](The-PowerShellTab-Object.md)-Klasse.

## <a name="psisecurrentvisiblehorizontaltool"></a>$psISE.CurrentVisibleHorizontalTool

Das **$psISE.CurrentVisibleHorizontalTool**-Objekt ist eine Instanz der [ISEAddOnTool](The-ISEAddOnTool-Object.md)-Klasse.
Es stellt das installierte Add-On-Tool dar, das derzeit am oberen Rand des Windows PowerShell ISE-Fensters angedockt ist.

## <a name="psisecurrentvisibleverticaltool"></a>$psISE.CurrentVisibleVerticalTool

Das **$psISE.CurrentVisibleHorizontalTool**-Objekt ist eine Instanz der [ISEAddOnTool](The-ISEAddOnTool-Object.md)-Klasse.
Es stellt das installierte Add-On-Tool dar, das derzeit am rechten Rand des Windows PowerShell ISE-Fensters angedockt ist.

## <a name="psiseoptionsthe-iseoptions-objectmd"></a>[$psISE.Options](The-ISEOptions-Object.md)

Das **$psISE.Options**-Objekt ist eine Instanz der [ISEOptions](The-ISEOptions-Object.md)-Klasse.
Das ISEOptions-Objekt stellt verschiedene Einstellungen für Windows PowerShell ISE dar.
Es ist eine Instanz der Microsoft.PowerShell.Host.ISE.ISEOptions-Klasse.

## <a name="psisepowershelltabsthe-powershelltabcollection-objectmd"></a>[$psISE.PowerShellTabs](The-PowerShellTabCollection-Object.md)

Das **$psISE.PowerShellTabs**-Objekt ist eine Instanz der [PowerShellTabCollection](The-PowerShellTabCollection-Object.md)-Klasse.
Es ist eine Sammlung aller zurzeit geöffneten PowerShell-Registerkarten, die die verfügbaren Windows PowerShell-Ausführungsumgebungen auf dem lokalen Computer oder auf verbundenen Remotecomputern darstellen. Jedes Element in der Sammlung ist eine Instanz der [PowerShellTab](The-PowerShellTab-Object.md)-Klasse.

## <a name="see-also"></a>Weitere Informationen
- [Das Windows PowerShell ISE-Skriptobjektmodell](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Referenz zum Windows PowerShell ISE-Objektmodell](Windows-PowerShell-ISE-Object-Model-Reference.md)
