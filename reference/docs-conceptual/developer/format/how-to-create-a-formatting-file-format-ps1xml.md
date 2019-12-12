---
title: Erstellen einer Formatierungs Datei (. Format. ps1xml) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72363619"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a>Erstellen einer Formatierungsdatei (.format.ps1xml)

In diesem Thema wird beschrieben, wie eine Formatierungs Datei (. Format. ps1xml) erstellt wird.

> [!NOTE]
> Sie können auch eine Formatierungs Datei erstellen, indem Sie eine Kopie einer der von Windows PowerShell bereitgestellten Dateien erstellen. Wenn Sie eine Kopie einer vorhandenen Datei erstellen, löschen Sie die vorhandene digitale Signatur, und fügen Sie der neuen Datei Ihre eigene Signatur hinzu.

### <a name="to-create-a-formatps1xml-file"></a>Zum Erstellen einer. Format. ps1xml-Datei.

1. Erstellen Sie eine Textdatei (. txt) mit einem Text-Editor, z. b. Notepad.

2. Kopieren Sie die folgenden Zeilen in die Formatierungs Datei.

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - Mit dem \<Konfigurations >\</Konfiguration > Tags wird der Stamm `Configuration` Knoten definiert. Alle zusätzlichen XML-Tags werden in diesen Knoten eingeschlossen.

   - Die <ViewDefinitions></ViewDefinitions> Tags definieren den `ViewDefinitions` Knoten. Alle Sichten werden innerhalb dieses Knotens definiert.

3. Speichern Sie die Datei im Installationsordner von Windows PowerShell, in Ihrem Modul Ordner oder in einem Unterordner des Modul Ordners. Verwenden Sie das folgende Namensformat, wenn Sie die Datei speichern: `MyFile.format.ps1xml`. Beim Formatieren von Dateien muss die `.format.ps1xml` Erweiterung verwendet werden.

   Nun können Sie der Formatierungs Datei Ansichten hinzufügen. Es gibt keine Beschränkung für die Anzahl der Sichten, die in einer Formatierungs Datei definiert werden können. Sie können eine einzelne Ansicht für jedes Objekt, mehrere Ansichten für dasselbe Objekt oder eine einzelne Ansicht hinzufügen, die von mehreren Objekten verwendet wird.

## <a name="see-also"></a>Weitere Informationen

[Schreiben einer Windows PowerShell-Formatierungs-und-Typen Datei](./writing-a-powershell-formatting-file.md)
