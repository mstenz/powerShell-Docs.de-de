---
title: Hinzufügen von Cmdlet-Namen und -Übersicht zu einem Cmdlet-Hilfethema
ms.date: 09/13/2016
ms.openlocfilehash: 399defcb596ff9e9a596f4cd25ebcb6bcb7c34d2
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86892879"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a>Hinzufügen von Cmdlet-Namen und -Übersicht zu einem Cmdlet-Hilfethema

In diesem Abschnitt wird beschrieben, wie Sie Inhalte hinzufügen, die in den Abschnitten " **Name** " und " **Synopsis** " der Cmdlet-Hilfe angezeigt werden. In der Hilfedatei wird dieser Inhalt dem Befehls Knoten für jedes Cmdlet hinzugefügt.

> [!NOTE]
> Eine umfassende Ansicht einer Hilfedatei erhalten Sie, indem Sie eine der `dll-Help.xml` Dateien im PowerShell-Installationsverzeichnis öffnen. Die `Microsoft.PowerShell.Commands.Management.dll-Help.xml` Datei enthält z. b. Inhalte für mehrere PowerShell-Cmdlets.

## <a name="to-add-the-cmdlet-name-and-a-synopsis"></a>So fügen Sie den Cmdlet-Namen und eine Synchronisierungs Datei hinzu

- Die Cmdlet-Hilfe kann zwei Beschreibungen für das Cmdlet anzeigen. Die erste Beschreibung ist eine kurze Beschreibung, die als Synopsis bezeichnet wird. Die zweite Beschreibung ist eine ausführlichere Beschreibung, die im [Thema Hinzufügen der ausführlichen Beschreibung zu einem Cmdlet-Hilfethema](./how-to-add-a-cmdlet-description.md)erläutert wird.
  Beide Beschreibungen sollten als einzelner Absatz geschrieben werden.

- Wiederholen Sie in der Synchronisierungs Datei den Namen des Cmdlets nicht. Der Benutzer wird darüber informiert, dass das `Get-Server` Cmdlet einen Server erhält, aber nicht informativ ist. Verwenden Sie stattdessen Synonyme, und fügen Sie der Beschreibung Details hinzu.

  Beispiel: "Ruft ein Objekt ab, das einen lokalen oder Remote Computer darstellt."

- Verwenden Sie einfache Verben wie "Get", "Create" und "Change" in der Synchronisierungs Datei. Vermeiden Sie die Verwendung von "Set", da sie ungenau ist, und achten Sie auf die Verwendung von "ändern".

  Beispiel: "Ruft Informationen über die Authenticode-Signatur in einer Datei ab."

- Schreiben Sie in die aktive Sprache. Beispiel: "verwenden Sie das TimeSpan-Objekt..." ist viel klarer als "das TimeSpan-Objekt kann verwendet werden..."

- Vermeiden Sie das Verb "Display", wenn Sie Cmdlets beschreiben, die Objekte erhalten. Obwohl in Windows PowerShell Cmdlet-Daten angezeigt werden, ist es wichtig, Benutzer zu dem Konzept zu bringen, das vom Cmdlet zurückgegeben wird, .NET Framework Objekte, deren Daten möglicherweise nicht angezeigt werden. Wenn Sie die Anzeige hervorheben, erkennt der Benutzer möglicherweise nicht, dass das Cmdlet möglicherweise viele andere nützliche Eigenschaften und Methoden zurückgegeben hat, die nicht angezeigt werden.

## <a name="see-also"></a>Weitere Informationen

[Windows PowerShell SDK](../windows-powershell-reference.md)
