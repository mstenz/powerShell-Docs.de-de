---
ms.date: 12/12/2018
keywords: DSC,PowerShell,Konfiguration,Setup,Einrichtung
title: Verpacken und Hochladen von Ressourcen auf einen Pullserver
ms.openlocfilehash: 8aac343d7495ecda94ed76d1d97079397eecd65f
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2020
ms.locfileid: "78278499"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a>Verpacken und Hochladen von Ressourcen auf einen Pullserver

Die folgenden Abschnitte gehen davon aus, dass Sie bereits einen Pullserver eingerichtet haben. Wenn Sie noch keinen Pullserver eingerichtet haben, können Sie die folgenden Anleitungen verwenden:

- [Einrichten eines DSC-SMB-Pullservers](pullServerSmb.md)
- [Einrichten eines DSC-HTTP-Pullservers](pullServer.md)

Jeder Zielknoten kann zum Herunterladen von Konfigurationen, Ressourcen und sogar zum Berichten seines Status konfiguriert werden. Dieser Artikel zeigt Ihnen, wie Sie Ressourcen hochladen können, damit sie zum Download zur Verfügung stehen, und wie Sie Clients so konfigurieren, dass sie Ressourcen automatisch herunterladen. Wenn der Knoten eine zugewiesene Konfiguration empfängt (durch **Pull** oder **Push** (v5)), lädt er automatisch alle für die Konfiguration erforderlichen Ressourcen vom in LCM angegebenen Speicherort herunter.

## <a name="package-resource-modules"></a>Verpacken von Ressourcenmodulen

Jede Ressource, die für einen Client zum Herunterladen verfügbar ist, muss in einer ZIP-Datei gespeichert werden. Das folgende Beispiel zeigt die erforderlichen Schritte unter Verwendung der Ressource [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0).

> [!NOTE]
> Wenn ein Client PowerShell 4.0 verwendet, müssen Sie die Ressourcenordnerstruktur vereinfachen und alle Versionsordner entfernen. Weitere Informationen finden Sie unter [Mehrere Ressourcenversionen](../configurations/import-dscresource.md#multiple-resource-versions).

Sie können das Ressourcenverzeichnis mit einem beliebigen Hilfsprogramm, einem Skript oder einer beliebigen Methode komprimieren. Unter Windows können Sie *mit der rechten Maustaste* auf das Verzeichnis „xPSDesiredStateConfiguration“ klicken und dann „Senden an“ und „Komprimierter Ordner“ auswählen.

![Rechtsklick](media/package-upload-resources/right-click.gif)

### <a name="naming-the-resource-archive"></a>Benennen des Ressourcenarchivs

Das Ressourcenarchiv muss im folgenden Format benannt werden:

```
{ModuleName}_{Version}.zip
```

Im Beispiel oben sollte „xPSDesiredStateConfiguration.zip“ in „xPSDesiredStateConfiguration_8.4.4.0.zip“ umbenannt werden.

### <a name="create-checksums"></a>Erstellen von Prüfsummen

Sobald das Ressourcenmodul komprimiert und umbenannt wurde, müssen Sie eine **Prüfsumme** erstellen.  Die **CheckSum** wird von LCM auf dem Client verwendet, um festzustellen, ob die Ressource geändert wurde und erneut heruntergeladen werden muss. Sie können mit dem Cmdlet **New-DSCCheckSum** eine [CheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) erstellen, wie im folgenden Beispiel gezeigt.

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

Es wird keine Ausgabe angezeigt, aber Sie sollten nun eine „xPSDesiredStateConfiguration_8.4.4.4.4.0.zip.zip.checksum“ vorfinden. Sie können auch `New-DSCCheckSum` für ein Verzeichnis mit Dateien mit dem Parameter `-Path` ausführen. Wenn bereits eine Prüfsumme vorhanden ist, können Sie mit dem Parameter `-Force` erzwingen, dass sie neu erstellt wird.

### <a name="where-to-store-resource-archives"></a>Speicherort für Ressourcenarchive

#### <a name="on-a-dsc-http-pull-server"></a>Auf einem DSC-HTTP-Pullserver

Wenn Sie Ihren HTTP-Pullserver einrichten (wie unter [Einrichten eines DSC-HTTP-Pullservers](pullServer.md) beschrieben), geben Sie Verzeichnisse für die Schlüssel **ModulePath** und **ConfigurationPath** an. Der Schlüssel **ConfigurationPath** gibt an, wo MOF-Dateien gespeichert werden sollen. **ModulePath** gibt an, wo DSC-Ressourcenmodule gespeichert werden sollen.

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a>Auf einer SMB-Freigabe

Wenn Sie eine **ResourceRepositoryShare** angegeben haben, speichern Sie beim Einrichten Ihres Pullclients Archive und Prüfsummen im Verzeichnis **SourcePath** aus dem Block **ResourceRepositoryShare**.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Configurations'
}

ResourceRepositoryShare SMBResourceServer
{
    SourcePath = '\\SMBPullServer\Resources'
}
```

Wenn Sie nur eine **ConfigurationRepositoryShare** angegeben haben, speichern Sie beim Einrichten Ihres Pullclients Archive und Prüfsummen im Verzeichnis **SourcePath** aus dem Block **ConfigurationRepositoryShare**.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a>Aktualisieren von Ressourcen

Sie können einen Knoten zwingen, seine Ressourcen zu aktualisieren, indem Sie die Versionsnummer im Namen des Archivs ändern oder eine neue Prüfsumme erstellen. Der Pullclient sucht nach neueren Versionen der erforderlichen Ressourcen sowie nach aktualisierten Prüfsummen, wenn sein LCM aktualisiert wird.

## <a name="see-also"></a>Weitere Informationen

- [Einrichten eines DSC-SMB-Pullservers](pullServerSmb.md)
- [Einrichten eines DSC-HTTP-Pullservers](pullServer.md)
