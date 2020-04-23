---
ms.openlocfilehash: 034d75a84e39cb0cf88a272ca58b5ccc229c5d9b
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "74540457"
---
# <a name="microsoft-open-source-code-of-conduct"></a>Microsoft Open-Source-Verhaltenskodex

Für dieses Projekt gelten die Microsoft-Verhaltensregeln für Open Source ([Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/)). Weitere Informationen finden Sie unter [Code of Conduct FAQ (FAQ zum Verhaltenskodex)](https://opensource.microsoft.com/codeofconduct/faq/). Alternativ können Sie sich mit weiteren Fragen und Kommentaren an [opencode@microsoft.com](mailto:opencode@microsoft.com) wenden.

[live-badge]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=live
[staging-badge]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=staging

## <a name="build-status"></a>Buildstatus

| Live-Branch | Staging-Branch |
|:------------|:---------------|
| [![live-badge][]][live-badge] | [![staging-badge][]][staging-badge]

## <a name="powershell-documentation"></a>PowerShell-Dokumentation

Willkommen im Repository der offiziellen PowerShell-Dokumentation.

## <a name="repository-structure"></a>Repository-Struktur

In diesem Repository befinden sich diese Ordner auf oberster Ebene, die jeweils eine Dokumentenmappe enthalten, die in der [Microsoft-Dokumentation](https://docs.microsoft.com/powershell) veröffentlicht wird.

- [/reference/](https://docs.microsoft.com/powershell/scripting/) ist für die konzeptuellen PowerShell-Themen und die Modulreferenz für die Versionen 5.1, 6.0 und 7.0 bestimmt. Dieser Inhalt ist auch die Quelle von Hilfeinhalten, die vom `Get-Help`-Cmdlet abgerufen werden.
  - [docs-conceptual/](https://docs.microsoft.com/powershell): Dieser Ordner enthält die konzeptionelle Dokumentation und die folgenden Dokumentationen:
    - [developer/](https://docs.microsoft.com/powershell/scripting/developer/) enthält die Dokumentation des PowerShell SDK (migriert von MSDN).
    - [dsc/](https://docs.microsoft.com/powershell/scripting/dsc/) ist für das Desired State Configuration-Feature bestimmt.
    - [gallery/](https://docs.microsoft.com/powershell/scripting/gallery) enthält den [PowerShell-Katalog](https://www.powershellgallery.com/).
    - [jea/](https://docs.microsoft.com/powershell/scripting/jea/) ist für das Feature „Just Enough Administration (JEA)“ bestimmt.
    - [/wmf](https://docs.microsoft.com/powershell/scripting/wmf/overview) enthält Versionshinweise für Windows Management Framework, das Paket, das für die Verteilung neuer Versionen von PowerShell an frühere Versionen von Windows verwendet wird.

## <a name="contributing"></a>Mitwirken

Beiträge zu diesem Repository werden aktiv über [Pullanforderungen](https://help.github.com/articles/using-pull-requests/) im *Staging*-Branch zusammengeführt.
Beachten Sie, dass Sie vor der Übermittlung einer Pullanforderung [einen Beitragslizenzvertrags unterschreiben](https://cla.microsoft.com/) müssen, um sicherzustellen, dass die Community Ihre Einsendungen kostenlos verwenden darf.

Weitere Informationen zu Beiträgen finden Sie in unserem [Handbuch für Mitwirkende](https://docs.microsoft.com/contribute/powershell/powershell-contribute). Das Handbuch für Mitwirkende enthält ausführliche Informationen zum Erstellen von Beiträgen zur Dokumentation, Stil- und Formatierungsvorgaben sowie Vorschlagen von Tools. Verwenden Sie die Vorlagen für Probleme und Pullanforderungen, um die Dokumentation über Versionen hinweg konsistent zu halten.

## <a name="licenses"></a>Lizenzen

Es gibt zwei Lizenzdateien für dieses Projekt. Die MIT-Lizenz gilt für den Code, der in diesem Repository enthalten ist. Die Creative Commons-Lizenz gilt für die Dokumentation.