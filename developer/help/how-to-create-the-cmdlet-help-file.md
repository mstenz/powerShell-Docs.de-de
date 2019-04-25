---
title: 'Vorgehensweise: Erstellen Sie die Cmdlet-Hilfedatei | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 08e05939f8aee42f2cd502a3da7a528d8460dec1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083245"
---
# <a name="how-to-create-the-cmdlet-help-file"></a>Erstellen der Cmdlet-Hilfedatei

In diesem Abschnitt wird beschrieben, wie Sie eine gültige XML-Datei zu erstellen, die Inhalt für Windows PowerShell-Cmdlet-Hilfethemen enthält. In diesem Abschnitt wird erläutert, wie Sie die Datei zu benennen, wie Sie die entsprechenden XML-Header hinzufügen und Gewusst wie: Hinzufügen von Knoten, die die verschiedenen Abschnitte der mit dem Cmdlet-Hilfe-Inhalt enthält.

> [!NOTE]
> Eine vollständige Übersicht der eine Hilfedatei öffnen eine der Dll-Help.xml Dateien im Installationsverzeichnis von Windows PowerShell gefunden. Beispielsweise enthält die Microsoft.PowerShell.Commands.Management.dll-Help.xml-Datei Inhalte für eine Reihe von Windows PowerShell-Cmdlets.

### <a name="how-to-create-a-cmdlet-help-file"></a>Vorgehensweise: erstellen eine Cmdlet-Hilfedatei

1. Erstellen Sie eine Textdatei, und speichern sie die mit UTF8-Codierung. Der Dateiname muss das folgende Format aufweisen, so, dass Windows PowerShell als ein Cmdlet-Hilfedatei erkannt werden können.

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. Fügen Sie die folgenden XML-Header in die Textdatei ein. Denken Sie daran, dass das Schema mit mehreren Agents Modeling Language (MAML) die Datei überprüft werden. Windows PowerShell bietet derzeit keine Tools zum Überprüfen der das.

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. Fügen Sie einen befehlsknoten der Cmdlet-Hilfedatei für die einzelnen Cmdlets in der Assembly hinzu. Jeder Knoten innerhalb des Knotens Befehl bezieht sich auf die verschiedenen Abschnitte der Cmdlet-Hilfethemas.

   Die folgende Tabelle enthält die XML-Element für jeden Knoten, gefolgt von einer Beschreibung der einzelnen Knoten.

   |Knoten|Beschreibung|
   |----------|-----------------|
   |`<details>`|Fügt Inhalt für die Abschnitte Namen und eine Zusammenfassung der Cmdlet-Hilfethemas hinzu. Weitere Informationen finden Sie unter [Gewusst wie: Hinzufügen der Cmdlet-Namen und die Zusammenfassung](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).|
   |`<maml:description>`|Fügt Inhalt für den Abschnitt "Beschreibung" der Cmdlet-Hilfethemas hinzu. Weitere Informationen finden Sie unter [die ausführliche Beschreibung zu einem Cmdlet-Hilfethemas hinzufügen](./how-to-add-a-cmdlet-description.md).|
   |`<command:syntax>`|Fügt Inhalt für den Abschnitt "SYNTAX" von der Cmdlet-Hilfethemas hinzu. Weitere Informationen finden Sie unter [wie hinzufügen-Syntax zu einem Cmdlet-Hilfethemas](./how-to-add-syntax-to-a-cmdlet-help-topic.md).|
   |`<command:parameters>`|Fügt Inhalt für die Cmdlet-Hilfethemas im Parameter-Abschnitt hinzu. Weitere Informationen finden Sie unter [wie Hinzufügen von Parametern zu einem Cmdlet-Hilfethemas](./how-to-add-parameter-information.md).|
   |`<command:inputTypes>`|Fügt Inhalt für den Abschnitt "EINGABEN" des Cmdlet-Hilfethemas hinzu. Weitere Informationen finden Sie unter [wie Eingabetypen hinzufügen zu einem Cmdlet-Hilfethemas](./how-to-add-input-types-to-a-cmdlet-help-topic.md).|
   |`<command:returnValues>`|Fügt Inhalt für den Abschnitt "OUTPUTS" der Cmdlet-Hilfethemas hinzu. Weitere Informationen finden Sie unter [wie Hinzufügen von Rückgabewerten zu einem Cmdlet-Hilfethemas](./how-to-add-return-values-to-a-cmdlet-help-topic.md).|
   |`<maml:alertset>`|Abschnitt "Hinweise" des Cmdlet-Hilfethemas wird Inhalt hinzugefügt. Weitere Informationen finden Sie unter [hinzufügen – Anmerkungen zu dieser zu einem Cmdlet-Hilfethemas](./how-to-add-notes-to-a-cmdlet-help-topic.md).|
   |`<command:examples>`|Fügt Inhalt für den Beispielabschnitt des Cmdlet-Hilfethemas hinzu. Weitere Informationen finden Sie unter [wie Beispielen hinzufügen zu einem Cmdlet-Hilfethemas](./how-to-add-examples-to-a-cmdlet-help-topic.md).|
   |`<maml:relatedLinks>`|Fügt Inhalt für den Abschnitt "Verwandte LINKS" des Cmdlet-Hilfethemas hinzu. Weitere Informationen finden Sie unter [wie verwandte Links hinzufügen, eine Cmdlet-Hilfethemas](./how-to-add-related-links-to-a-cmdlet-help-topic.md).|

## <a name="example"></a>Beispiel

 Hier ist ein Beispiel für einen befehlsknoten, der die Knoten für die verschiedenen Abschnitte der Cmdlet-Hilfethemas enthält.

```xml
<command:command
  xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
  xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
  <command:details>
    <!--Add name an synopsis here-->
  </command:details>
  <maml:description>
    <!--Add detailed description here-->
  </maml:description>
  <command:syntax>
    <!--Add syntax information here-->
  </command:syntax>
  <command:parameters>
    <!--Add parameter information here-->
  </command:parameters>
  <command:inputTypes>
    <!--Add input type information here-->
  </command:inputTypes>
  <command:returnValues>
    <!--Add return value information here-->
  </command:returnValues>
  <maml:alertSet>
    <!--Add Note information here-->
  </maml:alertSet>
  <command:examples>
    <!--Add cmdlet examples here-->
  </command:examples>
  <maml:relatedLinks>
    <!--Add links to related content here-->
  </maml:relatedLinks>
</command:command>
```

## <a name="see-also"></a>Weitere Informationen

 [So fügen Sie die Cmdlet-Namen und die Zusammenfassung hinzu](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [So fügen Sie die ausführliche Beschreibung zu einem Cmdlet-Hilfethema hinzu](./how-to-add-a-cmdlet-description.md)

 [So fügen Sie die Syntax für ein Cmdlet-Hilfethema hinzu](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Gewusst wie: Hinzufügen von Parametern zu einem Cmdlet-Hilfethema](./how-to-add-parameter-information.md)

 [Wie Sie eine Cmdlet-Hilfethemas Eingabetypen hinzufügen](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Rückgabe von Werten für ein Cmdlet-Hilfethema hinzufügen](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Gewusst wie: Hinzufügen – Anmerkungen dieser zu einem Cmdlet-Hilfethema](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Beispiele für ein Cmdlet-Hilfethema hinzufügen](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Gewusst wie: Hinzufügen von Links zu verwandten Themen zu einem Cmdlet-Hilfethema](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)