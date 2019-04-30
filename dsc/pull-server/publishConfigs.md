---
ms.date: 12/12/2018
keywords: dsc,powershell,configuration,setup
title: Veröffentlichen auf einem Pullserver mithilfe von Konfigurations-IDs (v4/v5)
ms.openlocfilehash: 0144fec43d7a8d65b79891567cc0dc3952175343
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079505"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a>Veröffentlichen auf einem Pullserver mithilfe von Konfigurations-IDs (v4/v5)

Die folgenden Abschnitte gehen davon aus, dass Sie bereits einen Pullserver eingerichtet haben. Wenn Sie noch keinen Pullserver eingerichtet haben, können Sie die folgenden Anleitungen verwenden:

- [Einrichten eines DSC-SMB-Pullservers](pullServerSmb.md)
- [Einrichten eines DSC-HTTP-Pullservers](pullServer.md)

Jeder Zielknoten kann zum Herunterladen von Konfigurationen, Ressourcen und sogar zum Berichten seines Status konfiguriert werden. Dieser Artikel zeigt Ihnen, wie Sie Ressourcen hochladen können, damit sie zum Download zur Verfügung stehen, und wie Sie Clients so konfigurieren, dass sie Ressourcen automatisch herunterladen. Wenn der Knoten eine zugewiesene Konfiguration empfängt (durch **Pull** oder **Push** (v5)), lädt er automatisch alle für die Konfiguration erforderlichen Ressourcen vom in LCM angegebenen Speicherort herunter.

## <a name="compile-configurations"></a>Kompilieren von Konfigurationen

Der erste Schritt beim Speichern von [Konfigurationen](../configurations/configurations.md) auf einem Pullserver besteht im Kompilieren der Dateien in MOF-Dateien. Damit eine Konfiguration generisch und auf mehrere Clients anwendbar wird, verwenden Sie `localhost` in Ihrem Node-Block. Das folgende Beispiel zeigt eine Konfigurationsshell, die `localhost` anstelle eines bestimmten Clientnamens verwendet.

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

Sobald Sie Ihre generische Konfiguration erstellt haben, sollten Sie über eine Datei „localhost.mof“ verfügen.

## <a name="renaming-the-mof-file"></a>Umbenennen der MOF-Datei

Sie können MOF-Konfigurationsdateien auf einem Pullserver mithilfe von **ConfigurationName** oder **ConfigurationID** speichern. Je nachdem, wie Sie die Einrichtung Ihrer Pullclients planen, können Sie einen der folgenden Abschnitte auswählen, um Ihre kompilierten MOF-Dateien ordnungsgemäß umzubenennen.

### <a name="configuration-ids-guid"></a>Konfigurations-IDs (GUIDs)

Sie müssen Ihre Datei „localhost.mof“ in „<GUID>.mof“ umbenennen. Sie können eine zufällige **GUID** mithilfe des folgenden Beispiels oder des Cmdlets [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) erstellen.

```powershell
[System.Guid]::NewGuid()
```

Beispielausgabe

```output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

Sie können Ihre MOF-Datei dann mit jeder zulässigen Methode umbenennen. Im folgenden Beispiel wird das Cmdlet [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) verwendet.

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

Weitere Informationen zur Verwendung von **GUIDs** in Ihrer Umgebung finden Sie unter [Plan for Guids (Planen von GUIDs)](/powershell/dsc/secureserver#guids).

### <a name="configuration-names"></a>Konfigurationsnamen

Sie müssen Ihre Datei „localhost.mof“ in „<Configuration Name>.mof“ umbenennen. Im folgenden Beispiel wird der Konfigurationsname aus dem vorherigen Abschnitt verwendet. Sie können Ihre MOF-Datei dann mit jeder zulässigen Methode umbenennen. Im folgenden Beispiel wird das Cmdlet [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) verwendet.

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a>Erstellen der Prüfsumme

Jede MOF-Datei, die auf einem Pullserver oder in einer SMB-Freigabe gespeichert ist, muss über eine zugehörige CHECKSUM-Datei verfügen. Diese Datei informiert Clients darüber, wenn sich die zugehörige MOF-Datei geändert hat und erneut heruntergeladen werden sollte.

Sie können mit dem Cmdlet [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) eine **CheckSum** erstellen. Sie können auch `New-DSCCheckSum` für ein Verzeichnis mit Dateien mit dem Parameter `-Path` ausführen. Wenn bereits eine Prüfsumme vorhanden ist, können Sie mit dem Parameter `-Force` erzwingen, dass sie neu erstellt wird. Das folgende Beispiel gibt ein Verzeichnis mit der MOF-Datei aus dem vorherigen Abschnitt an und verwendet den Parameter `-Force`.

```powershell
New-DscChecksum -Path '.\' -Force
```

Es wird keine Ausgabe angezeigt, aber es sollte nun eine Datei „<GUID or Configuration Name>.mof.checksum“ vorhanden sein.

## <a name="where-to-store-mof-files-and-checksums"></a>Speicherort für MOF-Dateien und Prüfsummen

### <a name="on-a-dsc-http-pull-server"></a>Auf einem DSC-HTTP-Pullserver

Wenn Sie Ihren HTTP-Pullserver einrichten (wie unter [Einrichten eines DSC-HTTP-Pullservers](pullServer.md) beschrieben), geben Sie Verzeichnisse für die Schlüssel **ModulePath** und **ConfigurationPath** an. Der Schlüssel **ConfigurationPath** gibt an, wo MOF-Dateien gespeichert werden sollen. **ConfigurationPath** gibt an, wo MOF- und CHECKSUM-Dateien gespeichert werden sollen.

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

Wenn Sie einen Pullclient für die Verwendung einer SMB-Freigabe einrichten, geben Sie eine **ConfigurationRepositoryShare** an. Alle MOF- und CHECKSUM-Dateien sollten dann im Verzeichnis **SourcePath** aus dem **ConfigurationRepositoryShare**-Block gespeichert werden.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a>Nächste Schritte

Im nächsten Schritt müssen Sie die Pullclients so konfigurieren, dass sie die angegebene Konfiguration pullen. Weitere Informationen finden Sie in einem der folgenden Leitfäden:

- [Einrichten eines Pullclients mithilfe von Konfigurations-IDs (v4)](pullClientConfigId4.md)
- [Einrichten eines Pullclients mithilfe von Konfigurations-IDs (v5)](pullClientConfigId.md)
- [Einrichten eines Pullclients mithilfe von Konfigurationsnamen (v5)](pullClientConfigNames.md)

## <a name="see-also"></a>Siehe auch

- [Einrichten eines DSC-SMB-Pullservers](pullServerSmb.md)
- [Einrichten eines DSC-HTTP-Pullservers](pullServer.md)
- [Verpacken und Hochladen von Ressourcen auf einen Pullserver](package-upload-resources.md)
