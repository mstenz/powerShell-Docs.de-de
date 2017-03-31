## <a name="microsoft-open-source-code-of-conduct"></a>Microsoft Open-Source-Verhaltenskodex

Dieses Projekt hat den [Microsoft Open Source Code of Conduct (Microsoft Open-Source-Verhaltenskodex)](https://opensource.microsoft.com/codeofconduct/) übernommen.
Weitere Informationen finden Sie unter [Code of Conduct FAQ (FAQ zum Verhaltenskodex)](https://opensource.microsoft.com/codeofconduct/faq/). Alternativ können Sie sich mit weiteren Fragen und Kommentaren an [opencode@microsoft.com](mailto:opencode@microsoft.com) wenden.

[![Buildstatus](https://ci.appveyor.com/api/projects/status/onshefxnc4g4pv87/branch/staging?svg=true)](https://ci.appveyor.com/project/PowerShell/powershell-docs/branch/staging)

# <a name="powershell-documentation"></a>PowerShell-Dokumentation

Willkommen im Repository der PowerShell-Dokumente, das die offizielle Windows PowerShell-Dokumentation enthält. 

## <a name="repository-structure"></a>Repository-Struktur
Jeder Ordner in diesem Repository wird in [MSDN](https://msdn.microsoft.com/en-us/powershell) veröffentlicht. Die Ordner entsprechen dem folgenden PowerShell-Bestand:
* [/dsc/](https://msdn.microsoft.com/en-us/powershell/dsc/) für die Funktion Desired State Configuration
* [/gallery/](https://msdn.microsoft.com/powershell/gallery) für den [PowerShell-Katalog](https://www.powershellgallery.com/)
* [/jea/](https://msdn.microsoft.com/powershell/jea/) für die Funktion Just Enough Administration
* [/reference/](https://msdn.microsoft.com/powershell/reference/) für den PowerShell-Modulverweis für die Versionen 2.0, 3.0, 4.0, 5.0, 5.1 und 6.0
  * Dieser Inhalt wird zukünftig durch das Cmdlet `Get-Help` aufgerufen
* [/scripting/](https://msdn.microsoft.com/en-us/powershell/scripting/) für das allgemeine PowerShell-Referenzmaterial
* [/wmf](https://msdn.microsoft.com/en-us/powershell/wmf/readme) enthält Versionshinweise für Windows Management Framework, das Paket, das für die Verteilung neuer Versionen von PowerShell an frühere Versionen von Windows verwendet wird. 



## <a name="contributing"></a>Beiträge

Beiträge zu diesem Repository werden aktiv über [Pullanforderungen](https://help.github.com/articles/using-pull-requests/) im *Staging*-Branch zusammengeführt. Beachten Sie, dass Sie vor der Übermittlung einer Pullanforderung [einen Beitragslizenzvertrags unterschreiben](https://cla.microsoft.com/) müssen, um sicherzustellen, dass die Community Ihre Einsendungen kostenlos verwenden darf.
Weitere Informationen zu Beiträgen finden Sie in unserem [Handbuch über Beiträge](CONTRIBUTING.md).
Lesen Sie sich den [-Styleguide für Entwürfe](./style.md) durch, bevor Sie Beiträge erstellen.
Verwenden Sie die Vorlagen für Probleme und Pullanforderungen, um die Dokumentation über Versionen hinweg konsistent zu halten. 
