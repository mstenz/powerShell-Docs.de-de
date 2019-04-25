---
title: 'Gewusst wie: Hinzufügen einer Cmdlet-Beschreibung | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083517"
---
# <a name="how-to-add-a-cmdlet-description"></a>Hinzufügen einer Cmdlet-Beschreibung

In diesem Abschnitt wird beschrieben, wie Inhalte hinzufügen, die in den Abschnitt "Beschreibung", der die Cmdlet-Hilfe angezeigt wird. Dieser Inhalt wird in der Hilfedatei befehlsknoten für jedes Cmdlet hinzugefügt.

> [!NOTE]
> Eine vollständige Übersicht der eine Hilfedatei öffnen eine der Dll-Help.xml Dateien im Installationsverzeichnis von Windows PowerShell gefunden. Beispielsweise enthält die Microsoft.PowerShell.Commands.Management.dll-Help.xml-Datei Inhalte für eine Reihe von Windows PowerShell-Cmdlets.

### <a name="to-add-a-description"></a>Eine Beschreibung hinzufügen

- Sie zunächst die grundlegenden Funktionen des-Cmdlets im Detail erläutert. In vielen Fällen können Sie die in den Cmdlet-Namen verwendeten Begriffe erläutert und unbekannten Konzepte anhand eines Beispiels veranschaulichen. Beispielsweise wenn Daten durch das Cmdlet in eine Datei angefügt wird, Erläutern Sie, dass es Daten an das Ende einer vorhandenen Datei hinzugefügt.

- Um alle Features des-Cmdlets zu suchen, lesen Sie in der Parameterliste. Beschreiben Sie die primäre Funktion des Cmdlets, und fügen Sie dann auf andere Funktionen und Features. Wenn die Hauptfunktion des-Cmdlets, einer Eigenschaft zu ändern, aber das-Cmdlet kann alle Eigenschaften ändern, z. B. dies in der detaillierten Beschreibung. Wenn Sie die Cmdlet-Parameter, die Benutzer auf unterschiedliche Weise Informationen anfordern können, erläutern.

- Enthalten Sie Informationen zu Möglichkeiten, Benutzer zusätzlich zu den offensichtlichen verwendet das Cmdlet verwenden können. Beispielsweise können Sie das Objekt, das die `Get-Host` Cmdlet abgerufen wird, um die Farbe des Texts in Windows PowerShell-Befehlsfenster zu ändern.

  Beispiel:  "Die `Get-Acl` Cmdlet ruft Objekte, die die Sicherheitsbeschreibung für eine Datei oder Ressource darstellen. Die Sicherheitsbeschreibung enthält die Zugriffssteuerungslisten (Access Control Lists, ACLs) der Ressource. Die ACL gibt die Berechtigungen, die Benutzer und Benutzergruppen Zugriff auf die Ressource."

- Die ausführliche Beschreibung sollte beschreiben, mit dem-Cmdlet, aber es sollte nicht beschreiben die Konzepte, die das Cmdlet verwendet. Platzieren Sie Konzept Definitionen in zusätzlichen hinweisen.

## <a name="see-also"></a>Weitere Informationen

[Windows PowerShell SDK](../windows-powershell-reference.md)
