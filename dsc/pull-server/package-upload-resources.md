---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Paket und Hochladen von Ressourcen mit einem Pullserver
ms.openlocfilehash: 29a62f96393a53c9e7da57a5e51732dcb0937194
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401238"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a>Paket und Hochladen von Ressourcen mit einem Pullserver

In den folgenden Abschnitten wird davon ausgegangen, dass Sie bereits einen Pull-Server eingerichtet haben. Wenn Sie Ihre Pull-Server nicht eingerichtet haben, können Sie die folgenden Handbüchern:

- [Einrichten eines DSC-SMB-Pullservers](pullServerSmb.md)
- [Einrichten eines DSC-HTTP-Pullservers](pullServer.md)

Jeder Zielknoten kann für das Herunterladen von Konfigurationen, Ressourcen und sogar meldet seinen Status konfiguriert werden. In diesem Artikel wird zeigen, wie Ressourcen hochladen, damit sie die heruntergeladen werden, und Konfigurieren von Clients zum automatischen Herunterladen von Ressourcen verfügbar sind. Zeitpunkt des Knotens eine zugewiesenen Konfiguration und empfängt, über **Pull** oder **Push** (v5), automatisch heruntergeladen von der Konfiguration aus dem Speicherort, die im LCM angegebene erforderlichen Ressourcen.

## <a name="package-resource-modules"></a>Paket-Ressourcenmodulen

Jede Ressource, die für einen Client zum Herunterladen verfügbar sind, muss in einer Datei ".zip" gespeichert werden. Das folgende Beispiel zeigt die erforderlichen Schritte, die mit der ["xpsdesiredstateconfiguration"](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) Ressource.

> [!NOTE]
> Wenn Sie Clients mithilfe von PowerShell 4.0 verfügen, Sie möchten bei Flaten die Ordnerstruktur für die Ressource und entfernen alle Ordner Version. Weitere Informationen finden Sie unter [mehrere Versionen der Ressource](../configurations/import-dscresource.md#multiple-resource-versions).

Sie können das Ressourcenverzeichnis mit jedem Hilfsprogramm, Skript oder -Methode, die Sie bevorzugen, komprimieren. In Windows, können Sie *mit der rechten Maustaste* für das Verzeichnis von "xPSDesiredStateConfiguration", und wählen Sie "Senden an", und klicken Sie dann "Komprimierten Ordner".

![Rechtsklick](../media/right-click.gif)

### <a name="naming-the-resource-archive"></a>Benennen das Archiv für die Ressource

Das Archiv für die Ressource muss mit dem folgenden Format benannt wird:

```
{ModuleName}_{Version}.zip
```

Im Beispiel oben sollte "xPSDesiredStateConfiguration.zip" umbenannte "xPSDesiredStateConfiguration_8.4.4.0.zip" sein.

### <a name="create-checksums"></a>Erstellen von Prüfsummen

Sobald das Ressourcenmodul komprimiert und umbenannt wurde, müssen Sie erstellen eine **Prüfsumme**.  Die **Prüfsumme** verwendet wird, durch den LCM auf dem Client, um festzustellen, ob die Ressource geändert wurde und muss erneut heruntergeladen werden. Sie erstellen eine **Prüfsumme** mit der [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) wie im folgenden Beispiel gezeigt.

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

Wird keine Ausgabe angezeigt werden, aber ein "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum" sollte nun angezeigt werden. Sie können auch ausführen `New-DSCCheckSum` für ein Verzeichnis mit Dateien, die mit der `-Path` Parameter. Wenn eine Prüfsumme bereits vorhanden ist, können Sie erzwingen, mit neu erstellt werden die `-Force` Parameter.

### <a name="where-to-store-resource-archives"></a>Speicherort für Archive der Ressource

#### <a name="on-a-dsc-http-pull-server"></a>Auf einem HTTP-Pullserver von DSC

Beim Einrichten Ihrer HTTP-Pullserver, siehe [richten Sie eine DSC-HTTP-Pullserver](pullServer.md), Verzeichnisse für die Angabe der **ModulePath** und **ConfigurationPath** Schlüssel. Die **ConfigurationPath** Schlüssel gibt an, in dem alle "MOF"-Dateien gespeichert werden sollen. Die **ModulePath** gibt an, in dem alle DSC-Ressourcenmodulen gespeichert werden sollen.

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

Wenn Sie angegeben haben eine **ResourceRepositoryShare**, wenn das Einrichten Ihrer Pull-Client speichern, Archive und Prüfsummen in der **SourcePath** des Verzeichnisses der **ResourceRepositoryShare** Block.

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

Wenn Sie nur angegeben ein **ConfigurationRepositoryShare**, wenn das Einrichten Ihrer Pull-Client speichern, Archive und Prüfsummen in der **SourcePath** des Verzeichnisses der  **ConfigurationRepositoryShare** Block.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a>Aktualisieren von Ressourcen

Sie können erzwingen, dass einen Knoten seine Ressourcen Änderung der Versionsnummer des Archivs Namen aktualisieren, oder indem Sie eine neue Prüfsumme zu erstellen. Der Pull-Client überprüft für neuere Versionen der erforderlichen Ressourcen sowie Prüfsummen, aktualisiert, wenn der LCM aktualisiert.

## <a name="see-also"></a>Siehe auch

- [Einrichten eines DSC-SMB-Pullservers](pullServerSmb.md)
- [Einrichten eines DSC-HTTP-Pullservers](pullServer.md)
