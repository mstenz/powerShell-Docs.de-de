---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configuration,setup
title: "DSC für Linux-Resource „nxArchive“"
ms.openlocfilehash: da647432e14d2a4a3ceb2a36c7dee2dbfd350116
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-for-linux-nxarchive-resource"></a>DSC für Linux-Resource „nxArchive“

Die Ressource **nxArchive** in PowerShell DSC bietet einen Mechanismus zum Entpacken von Archivdateien (.tar, .zip) in einem bestimmten Pfad auf einem Linux-Knoten.

## <a name="syntax"></a>Syntax

```
nxArchive <string> #ResourceName
{
    SourcePath = <string>
    DestinationPath = <string>
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Force = <bool> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>Eigenschaften

|  Eigenschaft |  Beschreibung | 
|---|---|
| SourcePath| Gibt den Quellpfad der Archivdatei an. Dies muss eine Datei des Typs „.tar“, „.zip“ oder „.tar.gz“ sein. | 
| DestinationPath| Gibt den Speicherort an, an dem der Archivinhalt einer Datei extrahiert werden soll.| 
| Checksum| Definiert den zu verwendenden Typ, wenn bestimmt wird, ob das Quellarchiv aktualisiert wurde. Werte sind: „ctime“, „mtime“ oder „md5“. Der Standardwert ist „md5“.| 
| Force| Bestimmte Dateioperationen (z. B. das Überschreiben einer Datei oder Löschen eines Verzeichnisses, das nicht leer ist), führen zu einem Fehler. Bei Verwenden der **Force**-Eigenschaft werden solche Fehler überschrieben. Der Standardwert ist **$false**.| 
| DependsOn | Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die **ID** des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, **ResourceName** und dessen Typ **ResourceType** ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.| 
| Ensure| Bestimmt, ob geprüft wird, ob der Inhalt der Archivdatei am **Ziel** vorhanden ist. Legen Sie diese Eigenschaft auf „Present“ fest, um sicherzustellen, dass der Inhalt vorhanden ist. Legen Sie sie auf „Absent“ fest, um sicherzustellen, dass der Inhalt nicht vorhanden ist. Der Standardwert ist „Present“.| 

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie Sie die Ressource **nxArchive** verwenden, um sicherzustellen, dass der Inhalt einer Archivdatei mit dem Namen `website.tar` vorhanden ist und an ein bestimmtes Ziel extrahiert wird.

```
Import-DSCResource -Module nx 

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = “http://release.contoso.com/releases/website.tar”
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = “mtime”
}

nxArchive SyncWebDir
{
   SourcePath = “/usr/release/staging/website.tar”
   DestinationPath = “/usr/local/apache2/htdocs/”
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
} 
```

