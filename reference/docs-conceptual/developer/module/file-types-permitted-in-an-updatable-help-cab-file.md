---
title: In einer aktualisierbaren Hilfe-CAB-Datei zulässige Dateitypen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: acabdb93-c41a-4b8d-acbe-45cdab91e198
caps.latest.revision: 10
ms.openlocfilehash: 3562804157ebdfca561445a8671d726b55cc4efd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367259"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a>Zulässige Dateitypen in aktualisierbaren CAB-Hilfedateien

In diesem Thema werden die Inhalts Anforderungen für die aktualisierbaren Hilfe-CAB-Dateien aufgelistet und beschrieben.

## <a name="updatable-help-cab-file-requirements"></a>Aktualisierbare Hilfe-CAB-Datei Anforderungen

Der Inhalt nicht komprimierter CAB-Dateien ist standardmäßig auf 1 GB beschränkt. Um diese Beschränkung zu umgehen, müssen die Benutzer den **Force** -Parameter der Cmdlets " [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) " und " [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) " verwenden.

Um die Sicherheit von Hilfedateien sicherzustellen, die aus dem Internet heruntergeladen werden, kann eine aktualisierbare CAB-Hilfedatei nur die unten aufgeführten Dateitypen enthalten. Das [Update-Help-](/powershell/module/Microsoft.PowerShell.Core/Update-Help) Cmdlet überprüft alle Dateien anhand der Hilfe Themen Schemas. Wenn das Cmdlet "`Update-Help`" auf eine Datei trifft, die ungültig ist oder kein zulässiger Typ ist, wird die ungültige Datei nicht installiert, und die Installation von Dateien aus dem CAB auf dem Computer des Benutzers wird beendet.

- XML-basierte Hilfe Themen für Cmdlets.

- XML-basierte Hilfe Themen für Skripts und Funktionen.

- XML-basierte Hilfe Themen für Windows PowerShell-Anbieter.

- Text basierte Hilfe Themen, z. b. Informationen zu Themen.

Mit [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) werden die CAB-Inhalte überprüft, wenn die CAB-Datei entpackt wird. Wenn `Update-Help` nicht kompatible Dateitypen in einer aktualisierbaren Hilfe-CAB-Datei findet, wird ein Beendigungs Fehler generiert, und der Vorgang wird beendet. Er installiert keine Hilfedateien aus dem CAB, auch die von kompatiblen Dateitypen.