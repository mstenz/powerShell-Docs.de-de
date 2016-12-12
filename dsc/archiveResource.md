---
title: "DSC-Ressourcen „Archive“"
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 77398d26f59975469e7c752a8d7f4f8bbbe4f553
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="dsc-archive-resource"></a>DSC-Ressourcen „Archive“

> Gilt für: Windows PowerShell 4.0, Windows PowerShell 5.0

Die Ressource „Archive“ in Windows PowerShell DSC bietet einen Mechanismus zum Entpacken von Archivdateien (.zip).

## <a name="syntax"></a>Syntax 
```MOF
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
}
```

## <a name="properties"></a>Eigenschaften

|  Eigenschaft  |  Beschreibung   | 
|---|---| 
| Ziel| Gibt den Speicherort an, an dem der Archivinhalt einer Datei extrahiert werden soll.| 
| Pfad| Gibt den Quellpfad der Archivdatei an.| 
| __Checksum__| Definiert den zu verwendenden Typ, wenn bestimmt wird, ob zwei Dateien identisch sind. Wenn __Checksum__ nicht angegeben ist, wird nur der Datei- oder Verzeichnisnamen für den Vergleich verwendet. Gültige Werte sind: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate, keine (Standard). Wenn Sie __Checksum__ ohne __Validate__ angeben, schlägt die Konfiguration fehl.| 
| Ensure| Bestimmt, ob geprüft wird, ob der Inhalt der Archivdatei am __Ziel__ vorhanden ist. Legen Sie diese Eigenschaft auf __Present__ fest, um sicherzustellen, dass der Inhalt vorhanden ist. Legen Sie sie auf __Absent__ fest, um sicherzustellen, dass der Inhalt nicht vorhanden ist. Der Standardwert ist __Present__.| 
| DependsOn | Gibt an, dass die Konfiguration einer anderen Ressource ausgeführt werden muss, bevor diese Ressource konfiguriert wird. Wenn beispielsweise die ID des Skriptblocks mit der Ressourcenkonfiguration, den Sie zuerst ausführen möchten, „ResourceName“ und dessen Typ __ResourceType__ ist, lautet die Syntax für das Verwenden dieser Eigenschaft `DependsOn = "[ResourceType]ResourceName"`.| 
| Überprüfen| Verwendet die Eigenschaft „Checksum“, um zu bestimmen, ob das Archiv der Signatur entspricht. Wenn Sie „Checksum“ ohne „Validate“ angeben, schlägt die Konfiguration fehl. Wenn Sie „Validate“ ohne „Checksum“ angeben, wird standardmäßig eine SHA-256-Prüfsumme verwendet.| 
| Force| Bestimmte Dateioperationen (z. B. das Überschreiben einer Datei oder Löschen eines Verzeichnisses, das nicht leer ist), führen zu einem Fehler. Bei Verwenden der Eigenschaften „Force“ werden solche Fehler überschrieben. Der Standardwert ist „False“.| 

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird veranschaulicht, wie Sie die Ressource „Archive“ verwenden, um sicherzustellen, dass der Inhalt einer Archivdatei mit dem Namen „Test.zip“ vorhanden ist und an ein bestimmtes Ziel extrahiert wird.

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
} 
```

