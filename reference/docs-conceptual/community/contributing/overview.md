---
title: Mitwirkung an der PowerShell-Dokumentation
description: Dieser Artikel bietet einen Überblick über die ersten Schritte als Mitwirkender an der PowerShell-Dokumentation.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 5db78ae2805cb26aa79aa698cfb8b5d8ba8911dc
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "79402627"
---
# <a name="contributing-to-powershell-documentation"></a>Mitwirkung an der PowerShell-Dokumentation

Vielen Dank für Ihre Unterstützung von PowerShell!

Der Leitfaden für Mitwirkende ist eine Sammlung von Artikeln, in denen die Tools und Prozesse erläutert werden, die wir bei Microsoft zum Erstellen der Dokumentation verwenden. Einige dieser Leitfäden enthalten Informationen, die für alle Dokumentationssätze gelten, die auf [docs.microsoft.com][docs] veröffentlicht werden. Einige der Leitfäden sind spezifisch für die Erstellung von Dokumentation für PowerShell.

Die allgemeinen Artikel finden Sie in unserer zentralen [Handbuch für Mitwirkende][contribute]. Die PowerShell-spezifischen Anleitungen sind hier verfügbar.

## <a name="ways-to-contribute"></a>Möglichkeiten zur Mitwirkung

Es gibt zwei Möglichkeiten zur Mitwirkung. Beide Formen sind für uns hilfreich.

- Das [Einreichen von Problemen][file-an-issue] hilft uns, Probleme und Lücken in unserer Dokumentation zu erkennen. Manchmal sind die Probleme schwierig zu beheben und erfordern weitere Untersuchungen und Recherchen. Der Issueprozess ermöglicht es uns, eine Unterhaltung über das Problem zu führen und eine befriedigende Lösung zu entwickeln.

- Das Einreichen neuer Inhalte oder Änderungen an vorhandenen Artikeln ist ein Prozess, der eine stärkere Einbindung mit sich bringt. Die folgenden Informationen beschreiben die Tools, Prozesse und Standards für das Einreichen von Inhalten für die Dokumentation.

## <a name="prepare-to-make-a-contribution"></a>Vorbereiten der Mitwirkung

Für die Mitwirkung an der Dokumentation ist ein GitHub-Konto erforderlich. Verwenden Sie die folgende Checkliste, um die Tools abzurufen und ein Verständnis der Prozesse zu erwerben, die wir für Beiträge verwenden.

1. [Registrieren Sie sich für GitHub](/contribute/get-started-setup-github)
1. [Installieren Sie die Git- und Markdown-Tools](/contribute/get-started-setup-tools)
1. [Installieren Sie das Docs Authoring Pack](/contribute/how-to-write-docs-auth-pack) (Paket zur Dokumenterstellung)
1. [Installieren Sie Posh-Git][posh-git] – nicht erforderlich, aber empfehlenswert
1. [Richten Sie ein lokales Git-Repository ein](/contribute/get-started-setup-local)
1. [Arbeiten Sie die Grundlagen von Git und GitHub durch](/contribute/git-github-fundamentals)

## <a name="get-started-writing-docs"></a>Erste Schritte mit dem Schreiben von Dokumentation

Es gibt zwei Möglichkeiten, Änderungen an der-Dokumentation beizutragen:

1. [Schnelle Bearbeitung vorhandener Dokumente](/contribute/#quick-edits-to-existing-documents)
   - Kleinere Korrekturen, Korrektur von Tippfehlern oder kleine Ergänzungen
1. [Vollständiger GitHub-Workflow für Dokumente](/contribute/how-to-write-workflows-major)
   - Große Änderungen, mehrere Versionen, Hinzufügen oder Ändern von Bildern oder Einreichung neuer Artikel

Lesen Sie darüber hinaus den Abschnitt [Writing essentials](/contribute/style-quick-start) (Grundlagen des Schreibens) des zentralen Handbuchs für Mitwirkende. Eine weitere hervorragende Ressource stellt der [Microsoft Writing Style Guide][style-guide] dar. Das Ziel des Microsoft Writing Style Guide besteht darin, Redakteure, technische Autoren, Entwickler, Marketingfachleute und alle anderen Personen in der IT beim Schreiben besserer Inhalte zu unterstützen.

Kleinere Korrekturen oder Klarstellungen an Dokumentation und Codebeispielen in öffentlichen Repositorys werden durch die [Nutzungsbedingungen][terms-of-use] von docs.microsoft.com abgedeckt.

Verwenden Sie den vollständigen GitHub-Workflow, wenn Sie erhebliche Änderungen vornehmen. Wenn Sie kein Microsoft-Mitarbeiter sind, führen erhebliche Änderungen zur Generierung eines Pull Requests, in dem Sie aufgefordert werden, online eine [Contribution Licensing Agreement (CLA)][cla] zu übermitteln. Sie müssen das Onlineformular ausfüllen, damit wir Ihren Pull Request überprüfen oder akzeptieren können.

## <a name="code-of-conduct"></a>Verhaltensregeln

Für alle Repositorys, die auf docs.microsoft.com- veröffentlichen, gilt der [Microsoft Open Source-Verhaltenskodex](https://opensource.microsoft.com/codeofconduct/) oder der [.NET Foundation-Verhaltenskodex](https://dotnetfoundation.org/code-of-conduct). Weitere Informationen finden Sie unter [Häufig gestellte Fragen zum Verhaltenskodex](https://opensource.microsoft.com/codeofconduct/faq/).

## <a name="next-steps"></a>Nächste Schritte

In den folgenden Artikeln werden spezifische Informationen zur PowerShell-Dokumentation behandelt. Wenn es Überschneidungen mit den allgemeinen Anleitungen im zentralen Handbuch für Mitwirkende gibt, weisen wir darauf hin, wie sich diese Regeln für PowerShell-Inhalte unterscheiden.

Lesen Sie die folgenden Dokumente:

- [Anlegen eines Eintrags](file-an-issue.md)
- [Erste Schritte mit dem Schreiben von Dokumentation](get-started-writing.md)
- [Übermitteln eines Pull Requests](pull-requests.md)
- [Styleguide für die PowerShell-Dokumentation](powershell-style-guide.md)
- [Bearbeiten der Cmdlet-Referenz](editing-cmdlet-ref.md)

Zusätzliche Ressourcen

- [Checkliste für die Bearbeitung](editorial-checklist.md)
- [Verwalten von Issues](managing-issues.md)
- [Verwalten von Pull Requests](managing-pull-requests.md)

<!--link refs-->
[cla]: https://cla.microsoft.com/
[contribute]: /contribute/
[docs]: https://docs.microsoft.com/
[file-an-issue]: file-an-issue.md
[posh-git]: https://www.powershellgallery.com/packages/posh-git
[psdocs]: https://docs.microsoft.com/powershell
[style-guide]: https://docs.microsoft.com/style-guide/welcome/
[terms-of-use]: https://docs.microsoft.com/legal/termsofuse