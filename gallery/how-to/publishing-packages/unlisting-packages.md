---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Entfernen von Paketen aus der Liste
ms.openlocfilehash: fb66fd23dae1d4640056a764c31426f61f56d910
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50003812"
---
# <a name="unlisting-packages"></a>Entfernen von Paketen aus der Liste

**Weshalb wird keine Option zum Entfernen von Paketen aus dem PowerShell-Katalog angezeigt?**

Der PowerShell-Katalog unterstützt nicht das endgültige Löschen von Paketen durch Benutzer.
So können andere Benutzer Abhängigkeiten von Ihren Paketen festlegen, ohne darauf zu achten, ob diese in Zukunft verfügbar sind.
Wenn das Pester-Modul z. B. vom Azure-Modul abhängt und das Azure-Modul aus dem Katalog entfernt wird, kann der Benutzer das Pester-Modul nicht mehr verwenden.

Anstatt ein Paket zu löschen, können Sie es jedoch aus der Liste entfernen.

**Was geschieht, wenn ein Paket aus der Liste im PowerShell-Katalog entfernt wird?**

Wenn ein Paket, z.B. ein Modul oder ein Skript, aus der Liste im PowerShell-Katalog entfernt wird, wird es nicht länger auf der Registerkarte „Pakete“ angezeigt. Außerdem werden aus der Liste entfernte Pakete nicht mehr über die Suchleiste gefunden.
Pakete, die aus der Liste entfernt wurden, können nur bei Angabe des genauen Namens und der Version des Pakets herunterladen werden.
Folglich treten infolge des Entfernens eines Pakets aus der Liste keine Probleme bei Modulen oder Skripts auf, die von diesem Paket abhängen.

Um Ihr Paket aus der Liste zu entfernen, rufen Sie die Seite „Paketdetails“ auf, und wählen Sie „Modul löschen“ aus. Deaktivieren Sie das Kontrollkästchen „Aufgelistet“, und klicken Sie auf „Speichern“.

**Wie kann ich ein Paket entfernen?**

Wenn ein Paket gelöscht werden muss, wenden Sie sich an die PowerShell-Katalogadministratoren.
In folgenden Fällen ist das Löschen eines Elements zulässig:
- Probleme aufgrund von Urheberrechtsverletzungen.
- Das Paket enthält potenziell schädlichen Inhalt.
- Das Paket enthält sensible Daten.

Um eine Anforderung zum Löschen eines Pakets an die PowerShell-Katalogadministratoren zu senden, wählen Sie auf der Seite „Paketdetails“ die Option „Support kontaktieren“ aus.
