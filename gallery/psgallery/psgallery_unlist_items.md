---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: PowerShell, Cmdlet, Katalog
ms.date: 2016-10-14
contributor: manikb
title: Entfernen von Elementen aus der Liste | MSDN
ms.technology: powershell
ms.openlocfilehash: ede07cce7b65b795f48d16cb2862880f84c3eda2
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="unlisting-items"></a>Entfernen von Elementen aus der Liste

**Weshalb ist keine Option zum Entfernen von Elementen aus dem PowerShell-Katalog verfügbar?**

Der PowerShell-Katalog bietet keine Unterstützung für das endgültige Löschen von Elementen durch Benutzer. So können andere Benutzer Abhängigkeiten von Ihren Elementen festlegen, ohne sich Gedanken darüber machen zu müssen, ob diese Elemente in der Zukunft verfügbar sind. Wenn das Pester-Modul z. B. vom Azure-Modul abhängt und das Azure-Modul aus dem Katalog entfernt wird, kann der Benutzer das Pester-Modul nicht mehr verwenden.

Anstatt ein Element zu löschen, können Sie es jedoch aus der Liste entfernen.

**Was geschieht, wenn ein Element aus der Liste im PowerShell-Katalog entfernt wird?**

Wenn ein Element, z. B. ein Modul oder ein Skript, aus der Liste des PowerShell-Katalogs entfernt wird, wird es nicht länger auf der Registerkarte „Elemente“ angezeigt.
Außerdem können Elemente, die aus der Liste entfernt wurden, nicht mehr über die Suchleiste gefunden werden.
Elemente, die aus der Liste entfernt wurden, können lediglich herunterladen werden, wenn der exakte Name und die Version des Elements angeben werden.
Folglich hat das Entfernen eines Elements aus der Liste nicht zur Folge, dass Probleme bei Modulen oder Skripts auftreten, die von diesem Element abhängen.

Um Ihr Element aus der Liste zu entfernen, wechseln Sie zur Seite mit den Elementdetails, und wählen Sie „Element löschen“. Deaktivieren Sie das Kontrollkästchen „Aufgelistet“, und klicken Sie auf „Speichern“.

**Wie kann ich ein Element entfernen?**

Wenn ein Element gelöscht werden muss, wenden Sie sich an die PowerShell-Katalogadministratoren.
In folgenden Fällen ist das Löschen eines Elements zulässig:
- Probleme aufgrund von Urheberrechtsverletzungen.
- Das Element enthält potenziell schädlichen Inhalt.
- Das Element enthält sensible Daten.

Um eine Anforderung zum Löschen eines Elements an die PowerShell-Katalogadministratoren zu senden, wählen Sie auf der Seite mit den Elementdetails die Option „Support kontaktieren“.  


