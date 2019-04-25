---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Löschen von Paketen
ms.openlocfilehash: ca5e68fcad52e4c7561d2c2b3858228652f22e0b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084163"
---
# <a name="deleting-packages"></a>Löschen von Paketen

Der PowerShell-Katalog unterstützt nicht das permanente Löschen von Paketen, da es dadurch bei jedem Benutzer zu Fehlern kommt, der diese Pakete unbedingt benötigt.

Stattdessen unterstützt der PowerShell-Katalog eine Möglichkeit zum Entfernen eines Pakets aus den Listen – dies erfolgt über die Paketverwaltungsseite auf der Website.
Wenn ein Paket aus den Listen entfernt ist, wird es in der Suche und den Paketlisten nicht mehr angezeigt. Dies gilt sowohl für den PowerShell-Katalog als auch für die PowerShellGet-Befehle.
Durch Angabe der genauen Version kann es jedoch weiterhin heruntergeladen werden, sodass automatisierte Skripts weiterhin funktionieren.

Wenn Sie in einer besonderen Situation der Ansicht sind, dass eines Ihrer Pakete gelöscht werden muss, kann dies durch das PowerShell-Katalogteam manuell durchgeführt werden.
Wenn beispielsweise ein Problem mit einer Urheberrechtsverletzung oder mit potenziell schädlichen Inhalten vorliegt, könnte ein berechtigter Grund für das Löschen des Elements vorliegen.
In diesem Fall sollten Sie über den [PowerShell-Katalog](http://www.PowerShellGallery.com) eine Supportanfrage senden.
