---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Veröffentlichen Sie auf einem Pull-Server mithilfe des Konfigurations-ID (v4/v5)
ms.openlocfilehash: 0144fec43d7a8d65b79891567cc0dc3952175343
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401313"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a>Veröffentlichen Sie auf einem Pull-Server mithilfe des Konfigurations-ID (v4/v5)

In den folgenden Abschnitten wird davon ausgegangen, dass Sie bereits einen Pull-Server eingerichtet haben. Wenn Sie Ihre Pull-Server nicht eingerichtet haben, können Sie die folgenden Handbüchern:

- [Einrichten eines DSC-SMB-Pullservers](pullServerSmb.md)
- [Einrichten eines DSC-HTTP-Pullservers](pullServer.md)

Jeder Zielknoten kann für das Herunterladen von Konfigurationen, Ressourcen und sogar meldet seinen Status konfiguriert werden. In diesem Artikel wird zeigen, wie Ressourcen hochladen, damit sie die heruntergeladen werden, und Konfigurieren von Clients zum automatischen Herunterladen von Ressourcen verfügbar sind. Zeitpunkt des Knotens eine zugewiesenen Konfiguration und empfängt, über **Pull** oder **Push** (v5), automatisch heruntergeladen von der Konfiguration aus dem Speicherort, die im LCM angegebene erforderlichen Ressourcen.

## <a name="compile-configurations"></a>Kompilieren von Konfigurationen

Der erste Schritt zum Speichern von [Konfigurationen](../configurations/configurations.md) auf einem Pull-Server ist in "MOF"-Dateien kompiliert. Um eine Konfiguration generisch und gilt für die mehr Clients zu machen, verwenden Sie `localhost` in Ihrer "Node"-Block. Das folgende Beispiel zeigt eine Konfiguration-Shell, die verwendet `localhost` anstelle eines bestimmten Client-Namens.

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

Nachdem Sie Ihre Konfiguration des generische kompiliert haben, sollten Sie eine Datei "localhost.mof" haben.

## <a name="renaming-the-mof-file"></a>Die MOF-Datei umbenennen

Sie können die Konfiguration "MOF"-Dateien auf einem Pull-Server durch Speichern **ConfigurationName** oder **ConfigurationID**. Je nachdem, wie Sie Ihre pullclients einrichten möchten können Sie einen Abschnitt unten, um Ihre kompilierten "MOF"-Dateien ordnungsgemäß zu benennen.

### <a name="configuration-ids-guid"></a>Konfigurations-ID (GUID)

Sie müssen Ihre "localhost.mof" Datei umbenennen "<GUID>.mof" Datei. Sie können einen zufälligen erstellen **Guid** verwenden Sie das Beispiel unten oder mithilfe der [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) Cmdlet.

```powershell
[System.Guid]::NewGuid()
```

Beispielausgabe

```output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

Sie können dann Ihre "MOF"-Datei, die mit einer akzeptablen Methode umbenennen. Im folgenden Beispiel wird die [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) Cmdlet.

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

Weitere Informationen zur Verwendung von **Guids** in Ihrer Umgebung finden Sie unter [Guids planen](/powershell/dsc/secureserver#guids).

### <a name="configuration-names"></a>Konfigurationsnamen

Sie müssen Ihre "localhost.mof" Datei umbenennen "<Configuration Name>.mof" Datei. Im folgenden Beispiel wird der Konfigurationsname aus dem vorherigen Abschnitt verwendet. Sie können dann Ihre "MOF"-Datei, die mit einer akzeptablen Methode umbenennen. Im folgenden Beispiel wird die [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) Cmdlet.

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a>Die Prüfsumme zu erstellen

Jedes "MOF"-Datei, die auf einem Pull-Server oder eine SMB-Freigabe muss eine zugeordnete ".checksum"-Datei gespeichert. Diese Datei ermöglicht Clients, die wissen, wann die zugeordnete "MOF"-Datei wurde geändert und erneut heruntergeladen werden soll.

Sie erstellen eine **Prüfsumme** mit der [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) Cmdlet. Sie können auch ausführen `New-DSCCheckSum` für ein Verzeichnis mit Dateien, die mit der `-Path` Parameter. Wenn eine Prüfsumme bereits vorhanden ist, können Sie erzwingen, mit neu erstellt werden die `-Force` Parameter. Im folgenden Beispiel wird ein Verzeichnis mit der Datei "MOF" aus dem vorherigen Abschnitt angegeben und verwendet die `-Force` Parameter.

```powershell
New-DscChecksum -Path '.\' -Force
```

Wird keine Ausgabe angezeigt werden, aber jetzt sollte eine "<GUID or Configuration Name>. mof.checksum" Datei.

## <a name="where-to-store-mof-files-and-checksums"></a>Speicherort für MOF-Dateien und Prüfsummen

### <a name="on-a-dsc-http-pull-server"></a>Auf einem HTTP-Pullserver von DSC

Beim Einrichten Ihrer HTTP-Pullserver, siehe [richten Sie eine DSC-HTTP-Pullserver](pullServer.md), Verzeichnisse für die Angabe der **ModulePath** und **ConfigurationPath** Schlüssel. Die **ConfigurationPath** Schlüssel gibt an, in dem alle "MOF"-Dateien gespeichert werden sollen. Die **ConfigurationPath** gibt an, in dem alle "MOF" und ".checksum"-Dateien gespeichert werden sollen.

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a>Auf einer SMB-Freigabe

Wenn Sie einen Pull-Client eingerichtet, eine SMB-Freigabe zu verwenden, geben Sie einen **ConfigurationRepositoryShare**. Alle "MOF" und ".checksum"-Dateien sollten dann in gespeichert werden die **SourcePath** des Verzeichnisses der **ConfigurationRepositoryShare** Block.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a>Nächste Schritte

Als Nächstes möchten Sie die Pull-Clients zum Abrufen der angegebenen Konfigurations konfigurieren. Weitere Informationen finden Sie in den folgenden Handbüchern:

- [Einrichten eines Pull-Clients mithilfe des Konfigurations-ID (v4)](pullClientConfigId4.md)
- [Einrichten eines Pull-Clients mithilfe des Konfigurations-ID (v5)](pullClientConfigId.md)
- [Einrichten eines Pull-Clients mithilfe von Konfigurationsnamen (v5)](pullClientConfigNames.md)

## <a name="see-also"></a>Siehe auch

- [Einrichten eines DSC-SMB-Pullservers](pullServerSmb.md)
- [Einrichten eines DSC-HTTP-Pullservers](pullServer.md)
- [Paket und Hochladen von Ressourcen mit einem Pullserver](package-upload-resources.md)
