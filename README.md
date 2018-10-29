# <a name="microsoft-open-source-code-of-conduct"></a>Microsoft Open-Source-Verhaltenskodex

Dieses Projekt hat den [Microsoft Open Source Code of Conduct (Microsoft Open-Source-Verhaltenskodex)](https://opensource.microsoft.com/codeofconduct/) übernommen.
Weitere Informationen finden Sie unter [Code of Conduct FAQ (FAQ zum Verhaltenskodex)](https://opensource.microsoft.com/codeofconduct/faq/). Alternativ können Sie sich mit weiteren Fragen und Kommentaren an [opencode@microsoft.com](mailto:opencode@microsoft.com) wenden.

[![Buildstatus](https://ci.appveyor.com/api/projects/status/onshefxnc4g4pv87/branch/staging?svg=true)](https://ci.appveyor.com/project/PowerShell/powershell-docs/branch/staging)

## <a name="powershell-documentation"></a>PowerShell-Dokumentation

Willkommen im Repository der offiziellen PowerShell-Dokumentation.

## <a name="repository-structure"></a>Repository-Struktur

In diesem Repository befinden sich diese Ordner auf oberster Ebene, die jeweils eine Dokumentenmappe enthalten, die in der [Microsoft-Dokumentation](https://docs.microsoft.com/powershell) veröffentlicht wird.

- [/developer/](https://docs.microsoft.com/powershell/developer/) enthält in Zukunft die Dokumentation des PowerShell SDKs
  - Diese Inhalte werden derzeit aus MSDN migriert.
- [/dsc/](https://docs.microsoft.com/powershell/dsc/) für die Funktion Desired State Configuration
- [/gallery/](https://docs.microsoft.com/powershell/gallery) für den [PowerShell-Katalog](https://www.powershellgallery.com/)
- [/jea/](https://docs.microsoft.com/powershell/jea/) für die Funktion Just Enough Administration
- [/reference/](https://docs.microsoft.com/powershell/scripting/) für die konzeptuellen Themen und den Modulverweis von PowerShell für die Versionen 3.0, 4.0, 5.0, 5.1 und 6.0.
  - Dieser Inhalt ist auch die Quelle von Hilfeinhalten, die vom `Get-Help`-Cmdlet abgerufen werden.
- [/wmf](https://docs.microsoft.com/powershell/wmf/readme) enthält Versionshinweise für Windows Management Framework, das Paket, das für die Verteilung neuer Versionen von PowerShell an frühere Versionen von Windows verwendet wird.

## <a name="contributing"></a>Beiträge

Beiträge zu diesem Repository werden aktiv über [Pullanforderungen](https://help.github.com/articles/using-pull-requests/) im *Staging*-Branch zusammengeführt.
Beachten Sie, dass Sie vor der Übermittlung einer Pullanforderung [einen Beitragslizenzvertrags unterschreiben](https://cla.microsoft.com/) müssen, um sicherzustellen, dass die Community Ihre Einsendungen kostenlos verwenden darf.

Weitere Informationen zu Beiträgen finden Sie in unserem [Handbuch für Mitwirkende](CONTRIBUTING.md).
Das Handbuch für Mitwirkende enthält ausführliche Informationen zum Erstellen von Beiträgen zur Dokumentation, Stil- und Formatierungsvorgaben sowie Vorschlagen von Tools.
Verwenden Sie die Vorlagen für Probleme und Pullanforderungen, um die Dokumentation über Versionen hinweg konsistent zu halten.

## <a name="licenses"></a>Lizenzen

Es gibt zwei Lizenzdateien für dieses Projekt.
Die MIT-Lizenz gilt für den Code, der in diesem Repository enthalten ist.
Die Creative Commons-Lizenz gilt für die Dokumentation.