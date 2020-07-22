---
title: Zulässige Dateitypen in aktualisierbaren CAB-Hilfedateien
ms.date: 03/22/2012
ms.openlocfilehash: 2a8e97edf8daaed915ea1a3e04565d996a2e15fd
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893134"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a>Zulässige Dateitypen in aktualisierbaren CAB-Hilfedateien

Der Inhalt nicht komprimierter CAB-Dateien ist standardmäßig auf 1 GB beschränkt. Um diese Beschränkung zu umgehen, müssen die Benutzer den **Force** -Parameter der Cmdlets " [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) " und " [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) " verwenden.

Um die Sicherheit von Hilfedateien sicherzustellen, die aus dem Internet heruntergeladen werden, kann eine aktualisierbare CAB-Hilfedatei nur die unten aufgeführten Dateitypen enthalten. Das [Update-Help-](/powershell/module/Microsoft.PowerShell.Core/Update-Help) Cmdlet überprüft alle Dateien anhand der Hilfe Themen Schemas. Wenn das `Update-Help` Cmdlet auf eine Datei trifft, die ungültig ist oder kein zulässiger Typ ist, wird die ungültige Datei nicht installiert, und die Installation von Dateien aus dem CAB auf dem Computer des Benutzers wird beendet.

- XML-basierte Hilfe Themen für Cmdlets.
- XML-basierte Hilfe Themen für Skripts und Funktionen.
- XML-basierte Hilfe Themen für PowerShell-Anbieter.
- Text basierte Hilfe Themen, z. b. Informationen zu Themen.

Mit [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) werden die CAB-Inhalte überprüft, wenn die CAB-Datei entpackt wird. Wenn `Update-Help` nicht kompatible Dateitypen in einer aktualisierbaren Hilfe-CAB-Datei findet, wird ein Beendigungs Fehler generiert und der Vorgang beendet. Er installiert keine Hilfedateien aus dem CAB, auch die von kompatiblen Dateitypen.
