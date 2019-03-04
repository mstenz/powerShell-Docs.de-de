---
title: In einem aktualisierbaren zulässigen Dateitypen unterstützen die CAB-Datei | Microsoft-Dokumentation
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
ms.openlocfilehash: 931383858c0b83f0a9a66026c215e16481b89e9e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862836"
---
# <a name="file-types-permitted-in-an-updatable-help-cab-file"></a>Zulässige Dateitypen in aktualisierbaren CAB-Hilfedateien

In diesem Thema aufgelistet und beschrieben von den Anforderungen für aktualisierbare Hilfe-CAB-Dateien.

## <a name="updatable-help-cab-file-requirements"></a>Anforderungen für aktualisierbare Hilfe-CAB-Datei

Nicht komprimierte Inhalt der CAB-Datei ist standardmäßig auf 1 GB beschränkt. Um diese Beschränkung zu umgehen, müssen Benutzer verwenden die **Force** Parameter, der die [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) und [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) Cmdlets.
Nicht komprimierte Inhalt der CAB-Datei ist standardmäßig auf 1 GB beschränkt. Um diese Beschränkung zu umgehen, müssen Benutzer verwenden die **Force** Parameter, der die [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) und [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) Cmdlets.

Um die Sicherheit der Hilfedateien zu gewährleisten, die aus dem Internet heruntergeladen werden, kann eine aktualisierbare Hilfe CAB-Datei nur die unten aufgeführten Dateitypen enthalten. Die [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) Cmdlet überprüft, ob alle Dateien anhand der Schemas Hilfethema. Wenn die `Update-Help` Cmdlet auftritt, eine Datei ist ungültig, oder ist kein zulässiger Typ ist, wird die ungültige Datei wird nicht installiert, und beendet die Installation von Dateien aus der CAB-Datei auf dem Computer des Benutzers.
Um die Sicherheit der Hilfedateien zu gewährleisten, die aus dem Internet heruntergeladen werden, kann eine aktualisierbare Hilfe CAB-Datei nur die unten aufgeführten Dateitypen enthalten. Die [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) Cmdlet überprüft, ob alle Dateien anhand der Schemas Hilfethema. Wenn die `Update-Help` Cmdlet auftritt, eine Datei ist ungültig, oder ist kein zulässiger Typ ist, wird die ungültige Datei wird nicht installiert, und beendet die Installation von Dateien aus der CAB-Datei auf dem Computer des Benutzers.

- XML-basierte Hilfethemen für Cmdlets.

- XML-Hilfethemen für Skripts und Funktionen.

- XML-basierte Hilfethemen für Windows PowerShell-Anbieter.

- Textbasierte Hilfethemen, z. B. über Themen.

Die [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) überprüft den Inhalt der CAB-Datei aus, wenn sie die CAB-Datei entpackt. Wenn `Update-Help` findet nicht kompatible Dateitypen in einer aktualisierbaren-CAB-Hilfekabinettdatei, generiert einen Fehler mit Abbruch und beendet den Vorgang. Hilfedateien werden aus der CAB-Datei, einschließlich der kompatiblen Dateitypen nicht installiert.
Die [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) überprüft den Inhalt der CAB-Datei aus, wenn sie die CAB-Datei entpackt. Wenn `Update-Help` findet nicht kompatible Dateitypen in einer aktualisierbaren-CAB-Hilfekabinettdatei, generiert einen Fehler mit Abbruch und beendet den Vorgang. Hilfedateien werden aus der CAB-Datei, einschließlich der kompatiblen Dateitypen nicht installiert.