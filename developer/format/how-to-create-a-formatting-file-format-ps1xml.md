---
title: 'Vorgehensweise: Erstellen Sie eine Formatierungsdatei (. ps1xml) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862966"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a>Erstellen einer Formatierungsdatei (.format.ps1xml)

In diesem Thema wird beschrieben, wie eine Formatierungsdatei zu erstellen (. ps1xml).

> [!NOTE]
> Sie können auch eine Formatierungsdatei erstellen, indem eine Kopie von einer der Dateien von Windows PowerShell bereitgestellt. Wenn Sie eine Kopie einer vorhandenen Datei vornehmen, löschen Sie die vorhandene digitale Signatur, und fügen Sie eigene Signatur in die neue Datei hinzu.

### <a name="to-create-a-formatps1xml-file"></a>Zum Erstellen einer. ps1xml-Datei.

1. Erstellen Sie eine Textdatei (.txt), die mit einem Text-Editor wie Editor.

2. Kopieren Sie die folgenden Zeilen in die Formatierungsdatei.

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - Die \<Configuration >\</Configuration > Tags definieren den Stamm `Configuration` Knoten. Alle zusätzlichen XML-Tags werden in diesem Knoten eingeschlossen sein.

   - Die <ViewDefinitions> </ViewDefinitions> Tags definieren die `ViewDefinitions` Knoten. Alle Ansichten werden in diesem Knoten definiert.

3. Speichern Sie die Datei, in den Installationsordner der Windows PowerShell, um Ihrem Ordner "Module" oder in einem Unterordner des Ordner "Module". Verwenden Sie das folgende Namensformat aus, wenn Sie die Datei speichern: `MyFile.format.ps1xml`. Formatierungsdateien verwenden, müssen die `.format.ps1xml` Erweiterung.

   Sie können jetzt die Formatierungsdatei Ansichten hinzu. Es gibt keine Beschränkung für die Anzahl der Aufrufe, die in einer Formatierungsdatei definiert werden können. Sie können eine einzelne Ansicht für jedes Objekt, mehrere Ansichten für das gleiche Objekt oder eine Ansicht, die von mehreren Objekten verwendet wird, hinzufügen.

## <a name="see-also"></a>Weitere Informationen

[Schreiben Sie eine Windows PowerShell, die Formatierung und Typen, Datei](./writing-a-powershell-formatting-file.md)
