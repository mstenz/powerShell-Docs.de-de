---
title: Einstieg in die Mitwirkung an PowerShell-Dokumentation
description: Dieser Artikel bietet einen Überblick über die ersten Schritte als Mitwirkender an der PowerShell-Dokumentation.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 95eb2c3157a99fcb6560914da8464022e1b64fad
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "79060305"
---
# <a name="get-started-contributing-to-powershell-documentation"></a>Einstieg in die Mitwirkung an PowerShell-Dokumentation

Dieser Artikel bietet einen Überblick über die ersten Schritte als Mitwirkender an der PowerShell-Dokumentation.

## <a name="powershell-docs-structure"></a>Struktur von „PowerShell-Docs“

Das [Repository „PowerShell-Docs“][psdocs] ist in zwei Inhaltsgruppen unterteilt. Git-Branches werden verwendet, um zu steuern, wie und wann Dokumentation veröffentlicht wird.

### <a name="reference-content"></a>Referenzinhalt

Der Referenzinhalt ist die PowerShell-Cmdlet-Referenz für die Cmdlets von PowerShell.
Die [Referenz][ref] wird in Versionsordnern (5.1, 6, 7.0 und 7.1) erfasst. Dieser Inhalt enthält nur die Cmdlet-Referenz für die von PowerShell gebotenen Module. Dieser Inhalt dient auch zum Erstellen der vom Cmdlet `Get-Help` angezeigten Hilfeinformationen.

> [!NOTE]
> Das Inhaltsverzeichnis für Referenzinhalte wird vom Veröffentlichungssystem automatisch generiert. Sie müssen das Inhaltsverzeichnis nicht aktualisieren.

### <a name="conceptual-content"></a>Konzeptionelle Inhalte

Die konzeptionelle Dokumentation umfasst folgenden Inhalt:

- Versionshinweise
- Einrichtungsanweisungen
- Beispielskripts und Anleitungen
- DSC-Dokumentation
- SDK-Dokumentation

Die [konzeptionelle Dokumentation][conceptual] ist nicht versionsbezogen organisiert. Alle Artikel werden für jede Version von PowerShell angezeigt. Wir arbeiten an der Erstellung versionsspezifischer Artikel. Sobald dieses Feature in unserer Dokumentation verfügbar ist, wird dieser Leitfaden mit den entsprechenden Informationen aktualisiert.

> [!NOTE]
> Jedes Mal, wenn ein konzeptioneller Artikel hinzugefügt, entfernt oder umbenannt wird, muss das Inhaltsverzeichnis aktualisiert und in den Pull Request aufgenommen werden.

## <a name="using-git-branches"></a>Verwenden von Git-Branches

Der Standardbranch für PowerShell-Docs ist `staging`. Änderungen, die in Bearbeitungsbranches vorgenommen werden, werden vor der Veröffentlichung in den Branch `staging` gemergt. Ca. einmal pro Woche wird der Branch `staging` in den Branch `live` gemergt. Der Branch `live` enthält den Inhalt, der auf docs.microsoft.com veröffentlicht wird. Änderungen dürfen auf keinen Fall im Branch `live` erfolgen.

Wenn Sie eine Dokumentationsänderung einreichen, die nur für eine unveröffentlichte Version von PowerShell gilt, prüfen Sie, ob es einen Releasebranch für diese Version gibt. Alle Änderungen, die sich auf eine bestimmte, künftige Version beziehen, sollten auf den Releasebranch abzielen. Releasebranches weisen das folgende Namensmuster auf: `release-<version>`.

Erstellen Sie vor dem Einleiten von Änderungen einen Bearbeitungsbranch in Ihrer lokalen Kopie des Repositorys „PowerShell-Docs“. Dies muss ein [Klon Ihrer Fork][fork] sein. Stellen Sie sicher, dass Sie Ihr lokales Repository synchronisieren, bevor Sie Ihren Bearbeitungsbranch erstellen. Der Bearbeitungsbranch muss aus einer aktualisierten Kopie des Branches `staging` oder `release` erstellt werden.

Nehmen Sie die einzureichenden Änderungen im Anschluss an den Prozess im Abschnitt [Durchführen von Änderungen][making-changes] im zentralen Leitfaden für Mitwirkende vor.

### <a name="creating-new-articles"></a>Erstellen neuer Artikel

Für jedes neue Dokument, an dem Sie mitwirken möchten, muss ein GitHub-Issue erstellt werden. Prüfen Sie auf bestehende Issues, um sicherzustellen, dass es nicht zu Überschneidungen kommt. Issues, die jemandem zugewiesen werden, gelten als „in Bearbeitung“. Wenn Sie an einem Issue mitarbeiten möchten, wenden Sie sich an die für das Issue zuständige Person.

Ähnlich wie beim [RFC-Prozess][rfc] für PowerShell stellt das Erstellen eines Issues vor dem Schreiben des Inhalts sicher, dass Sie nicht viel Zeit und Mühe für etwas aufwenden, das vom PowerShell-Docs-Team abgelehnt wird. Dies ermöglicht es uns auch, uns mit Ihnen über den Umfang des Inhalts zu beraten und darüber, wo er in die PowerShell-Dokumentation am besten passt.

### <a name="updating-existing-articles"></a>Aktualisieren vorhandener Artikel

Sofern zutreffend, werden Cmdlet-Referenzartikel in allen Versionen von PowerShell dupliziert. Wenn Sie ein Issue mit einer Cmdlet-Referenz oder einem `About_`-Artikel melden, müssen Sie angeben, welche Versionen vom Issue betroffen sind. Die Issuevorlage in GitHub enthält eine Checkliste mit den Versionen. Aktivieren Sie die Kontrollkästchen, um anzugeben, welche Versionen des Inhalts betroffen sind. Wenn Sie eine Änderung an einem Artikel zu einem Issue einreichen, das mehrere Versionen des Inhalts betrifft, müssen Sie die entsprechende Änderung auf jede Version der Datei anwenden.

## <a name="next-steps"></a>Nächste Schritte

Siehe [Übermitteln eines Pull Requests](pull-requests.md).

<!--link refs-->
[conceptual]: https://github.com/MicrosoftDocs/PowerShell-Docs/tree/staging/reference/docs-conceptual
[fork]: /contribute/get-started-setup-local#fork-the-repository
[making-changes]: /contribute/how-to-write-workflows-major#making-your-changes
[psdocs]: https://github.com/MicrosoftDocs/PowerShell-Docs
[ref]: https://github.com/MicrosoftDocs/PowerShell-Docs/tree/staging/reference
[rfc]: https://github.com/PowerShell/powershell-rfc/blob/master/RFC0000-RFC-Process.md