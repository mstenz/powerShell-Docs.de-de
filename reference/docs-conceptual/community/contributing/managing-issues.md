---
title: Verwalten von Issues
description: In diesem Artikel wird erläutert, wie das PowerShell-Docs-Team Pull Requests verwaltet.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: cd7aba83d42a6a2eba1ce73910fdd34096342c21
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/10/2020
ms.locfileid: "79060275"
---
# <a name="how-we-manage-issues"></a>Verwalten von Issues

In diesem Artikel wird beschrieben, wie Issues im Repository „PowerShell-Docs“ verwaltet werden. Dieser Artikel ist als Arbeitshilfe für Mitglieder des PowerShell-Docs-Teams gedacht. Er wird hier veröffentlicht, um den Prozess für unsere externen Mitwirkenden transparent zu gestalten.

## <a name="sources-of-issues"></a>Quellen von Issues

- Mitwirkende an der Community
- Interne Mitwirkende
- Transkriptionen von Kommentaren aus Kanälen in sozialen Medien
- Feedback über das Docs-Feedbackformular

## <a name="response-time-targets"></a>Zielzeit für Antworten

- Sichtung: 5 Werktage
- Korrektur oder Änderung – kein bestimmtes Ziel – nur bestmögliche Bestrebungen

### <a name="labeling--milestones"></a>Bezeichnung und Meilensteine

#### <a name="label-types"></a>Bezeichnungstypen

|Präfix  | BESCHREIBUNG                                                         |
|------- | --------------------------------------------------------------------|
|Bereich    | Dient zur Angabe des Teils von PowerShell oder der Dokumentation, der im Issue diskutiert wird.<br>Nützlich für Zuständige für Features, um Issues für ihr Feature zu finden.|
|Pri     | Wird verwendet, um die Priorität des Issues anzugeben. Wertebereich 0-4.        |
|Problem   | Dient zur Klassifizierung der Art des Feedbacks für das Issue                     |
|Überprüfung  | Wird für Issues verwendet, die eine weitere Überprüfung durch das Team erfordern              |
|Status  | Dient zum Angeben des Status des Arbeitselements                        |
|Warten | Dient als Hinweis darauf, dass wir auf etwas warten                   |

#### <a name="milestones"></a>Meilensteine

Issues und Pull Requests (PRs) müssen mit dem entsprechenden Meilenstein gekennzeichnet sein. Wenn das Issue nicht für eine bestimmte Version bestimmt ist, wird kein Meilenstein verwendet. Issues für Docs-PRs für Änderungen, die noch nicht in die PowerShell-Codebasis gemergt wurden, müssen dem Meilenstein **Zukunft** zugewiesen werden. Nachdem die Codeänderung gemergt wurde, ändern Sie den Meilenstein in die entsprechende Version.

|    Meilenstein     |                    BESCHREIBUNG                     |
| ---------------- | -------------------------------------------------- |
| 6.x              | Mit PowerShell 6.0 bis 6.2.x verknüpfte Arbeitselemente |
| 7.0.0            | Mit PowerShell 7.0 verknüpfte Arbeitselemente               |
| 7.1.0            | Mit PowerShell 7.1 verknüpfte Arbeitselemente               |
| Zukunft           | Arbeitselemente in einer zukünftigen Version von PowerShell          |
| PSReadline-vNext | Arbeitselemente in einer zukünftigen Version von PSReadline          |

## <a name="triage-process"></a>Sichtungsprozess

Das PowerShell-Dokumentationsteam trifft sich einmal pro Woche, um alle seit dem letzten Treffen hinzugekommenen Issues zu erörtern. Ein Issue gilt als gesichtet, wenn Bezeichnungen oder ein Zuständiger zugewiesen wurden. Die Mitglieder des PowerShell-Dokumentationsteams werden ermutigt, die Issues täglich zu prüfen und neue Issues zu sichten, sobald sie eingehen. Die wöchentliche Sichtungssitzung kann dann bei Bedarf dazu genutzt werden, die neuen Issues ausführlicher zu erörtern.

### <a name="misplaced-product-feedback"></a>Falsch gemeldetes Produktfeedback

- Geben Sie einen Kommentar für den Kunden ein, der angibt, dass es sich um Produktfeedback handelt, und fügen Sie einen Link zum entsprechenden Feedbackkanal hinzu.
- Optional: Kopieren Sie das Issue an die entsprechende Stelle für Produktfeedback, fügen Sie einen Link zu dem kopierten Element hinzu, und schließen Sie das Issue. Kopieren Sie Issues NICHT in UserVoice.

  | DocSet    | Produktfeedback-URL                                         |
  | --------- | ------------------------------------------------------------ |
  | developer | https://github.com/PowerShell/PowerShell/issues/new/choose   |
  | DSC       | https://windowsserver.uservoice.com/forums/301869-powershell |
  | Katalog   | https://github.com/powershell/powershellgallery/issues/new   |
  | jea       | https://github.com/powershell/jea/issues/new                 |
  | Referenz | https://github.com/PowerShell/PowerShell/issues/new/choose   |
  | wmf       | https://windowsserver.uservoice.com/forums/301869-powershell |

### <a name="support-requests"></a>Supportanfragen

- Wenn die Supportfrage einfach ist, beantworten Sie sie höflich, und schließen Sie das Issue.
- Wenn die Frage komplizierter ist oder der Fragensteller mit weiteren Fragen antwortet, leiten Sie ihn an Foren und Supportkanäle weiter. Vorgeschlagener Text für die Umleitung zu Foren:

    > Dies ist nicht das richtige Forum für diese Art von Fragen. Stellen Sie Ihre Frage besser in einem Supportforum der Community. Eine Liste der Communityforen finden Sie unter: https://docs.microsoft.com/powershell/scripting/community/community-support

### <a name="code-of-conduct-violations"></a>Verstöße gegen Verhaltensregeln

- Bearbeiten Sie das Issue, um ggf. anstößige Inhalte zu entfernen.
- Geben Sie einen Kommentar ein, dass es sich bei dem Issue um Spam handelt, schließen Sie das Issue, und sperren Sie es anschließend, um weitere Kommentare zu verhindern.
- Jedes Vorkommen sollte bei der wöchentlichen Sichtung besprochen werden, um den Bedarf an weiteren Maßnahmen festzustellen (Bericht an GitHub oder Microsoft Legal).
