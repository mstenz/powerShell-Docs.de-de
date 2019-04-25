---
title: Hinzufügen von der Cmdlet-Namen und eine Zusammenfassung zu einer Cmdlet-Hilfethemas | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083335"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a>Hinzufügen von Cmdlet-Namen und -Übersicht zu einem Cmdlet-Hilfethema

Dieser Abschnitt beschreibt, wie Sie Inhalte hinzufügen, die in den Abschnitten "NAME" und "Zusammenfassung" der Cmdlet-Hilfe angezeigt wird. Dieser Inhalt wird in der Hilfedatei befehlsknoten für jedes Cmdlet hinzugefügt.

> [!NOTE]
> Eine vollständige Übersicht der eine Hilfedatei öffnen eine der Dll-Help.xml Dateien im Installationsverzeichnis von Windows PowerShell gefunden. Beispielsweise enthält die Microsoft.PowerShell.Commands.Management.dll-Help.xml-Datei Inhalte für eine Reihe von Windows PowerShell-Cmdlets.

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a>Cmdlet-Namen und eine Zusammenfassung hinzufügen

- Die Cmdlet-Hilfe kann es sich um zwei Beschreibungen für das-Cmdlet anzeigen. Die erste Beschreibung ist eine kurze Beschreibung, die als die Zusammenfassung bezeichnet wird. Die zweite Beschreibung wird eine ausführlichere Beschreibung, die hier erörtert wird [hinzufügen die ausführliche Beschreibung zu einem Cmdlet-Hilfethemas](./how-to-add-a-cmdlet-description.md). Sowohl diese Beschreibungen sollte als einen einzelnen Absatz geschrieben werden.

- Wiederholen Sie in der Zusammenfassung nicht den Cmdlet-Namen ein. Den Benutzer darüber informiert, dass das Cmdlet Get-Server auf einen Server ruft ist kurz, aber nicht informativ. Stattdessen verwenden Sie die Synonyme und Hinzufügen von Details zu die Beschreibung.

  Beispiel: "Ruft ein Objekt, das einen lokalen Computer oder Remotecomputer darstellt."

- Verwenden Sie einfache Verben wie "get", "erstellen" und "ändern" aus, in der Zusammenfassung. Vermeiden Sie "set" da vage ist, und mit Effekten Wörter wie "ändern."

  Beispiel: "Ruft Informationen über die Authenticode-Signatur in einer Datei."

- Im aktiv geschrieben. Zum Beispiel "verwenden das TimeSpan-Objekt..." ist viel klarer als "das TimeSpan-Objekt, verwendet werden kann..."

- Vermeiden Sie das Verb "Display" aus, wenn die Cmdlets, die beschreibt, die Objekte zu erhalten. Obwohl Windows PowerShell Cmdlet Daten angezeigt wird, ist es wichtig, Computerbenutzer in das Konzept eingeführt, die mit dem Cmdlet die .NET Framework-Objekte zurückgegeben, deren Daten nicht angezeigt werden können. Wenn Sie die Anzeige zu verdeutlichen, kann der Benutzer nicht beachten Sie, dass möglicherweise mit dem-Cmdlet zurückgegeben wurden, viele andere nützliche Eigenschaften und Methoden, die nicht angezeigt werden.

## <a name="see-also"></a>Weitere Informationen

 [Windows PowerShell SDK](../windows-powershell-reference.md)