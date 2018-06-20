---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Die ISE-Objektmodellhierarchie
ms.openlocfilehash: 0159707b1050c412a74da3d3ca02a46cea982556
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30950691"
---
# <a name="the-ise-object-model-hierarchy"></a>Die ISE-Objektmodellhierarchie

In diesem Thema wird die Hierarchie der Objekte beschrieben, die Teil von Windows PowerShell Integrated Scripting Environment (ISE) sind.
Windows PowerShell ISE ist in Windows PowerShell 3.0 und in Windows PowerShell 4.0 enthalten.
Klicken Sie auf ein Objekt, um die Dokumentation für die Klasse aufzurufen, die das Objekt definiert.

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
Es ist eine Sammlung aller zurzeit geöffneten PowerShell-Registerkarten, die die verfügbaren Windows PowerShell-Ausführungsumgebungen auf dem lokalen Computer oder auf verbundenen Remotecomputern darstellen.
Jedes Element in der Sammlung ist eine Instanz der [PowerShellTab](The-PowerShellTab-Object.md)-Klasse.

## <a name="see-also"></a>Weitere Informationen

- [Zweck des Windows PowerShell ISE-Skriptobjektmodells](Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
- [Die ISE-Objektmodellhierarchie](The-ISE-Object-Model-Hierarchy.md)