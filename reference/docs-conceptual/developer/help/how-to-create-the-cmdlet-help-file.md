---
title: Erstellen der Hilfedatei für das Cmdlet | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 186a8ceecea47564503dc181a76cc314033b6d3f
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/04/2020
ms.locfileid: "76996034"
---
# <a name="how-to-create-the-cmdlet-help-file"></a>Erstellen der Cmdlet-Hilfedatei

In diesem Abschnitt wird beschrieben, wie Sie eine gültige XML-Datei erstellen, die Inhalt für Windows PowerShell-Cmdlet-Hilfe Themen enthält. In diesem Abschnitt wird erläutert, wie Sie die Hilfedatei benennen, die entsprechenden XML-Header hinzufügen und Knoten hinzufügen, die die verschiedenen Abschnitte der Cmdlet-Hilfe Inhalte enthalten.

> [!NOTE]
> Eine umfassende Übersicht über eine Hilfedatei erhalten Sie, indem Sie eine der dll-Help. XML-Dateien öffnen, die sich im Windows PowerShell-Installationsverzeichnis befinden. Beispielsweise enthält die Datei Microsoft. PowerShell. Commands. Management. dll-Help. XML Inhalte für mehrere der Windows PowerShell-Cmdlets.

### <a name="how-to-create-a-cmdlet-help-file"></a>Erstellen einer Cmdlet-Hilfedatei

1. Erstellen Sie eine Textdatei, und speichern Sie Sie mithilfe der UTF8-Codierung. Der Dateiname muss das folgende Format aufweisen, damit Windows PowerShell ihn als Cmdlet-Hilfedatei erkennen kann.

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. Fügen Sie die folgenden XML-Header der Textdatei hinzu. Beachten Sie, dass die Datei mit dem MAML-Schema (Multi-Agent Modeling Language) überprüft wird. Derzeit bietet Windows PowerShell keine Tools zum Überprüfen der Datei.

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. Fügen Sie der Cmdlet-Hilfedatei einen Befehls Knoten für jedes Cmdlet in der Assembly hinzu. Jeder Knoten im Befehls Knoten bezieht sich auf die verschiedenen Abschnitte des Cmdlet-Hilfe Themas.

   In der folgenden Tabelle wird das XML-Element für jeden Knoten aufgeführt, gefolgt von einer Beschreibung der einzelnen Knoten.

   |Knoten|Description|
   |----------|-----------------|
   |`<details>`|Fügt Inhalt für die Abschnitte "Name" und "Synopsis" des Cmdlet-Hilfe Themas hinzu. Weitere Informationen finden Sie unter Vorgehens [Weise beim Hinzufügen des Cmdlet-namens und der Synchronisierungs](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)Datei.|
   |`<maml:description>`|Fügt Inhalt für den Beschreibungs Abschnitt des Cmdlet-Hilfe Themas hinzu. Weitere Informationen finden Sie unter Vorgehens [Weise beim Hinzufügen der ausführlichen Beschreibung zu einem Cmdlet-Hilfethema](./how-to-add-a-cmdlet-description.md).|
   |`<command:syntax>`|Fügt Inhalt für den Syntax Abschnitt des Cmdlet-Hilfe Themas hinzu. Weitere Informationen finden Sie unter Vorgehens [Weise beim Hinzufügen von Syntax zu einem Cmdlet-Hilfethema](./how-to-add-syntax-to-a-cmdlet-help-topic.md).|
   |`<command:parameters>`|Fügt Inhalt für den Parameter Abschnitt des Cmdlet-Hilfe Themas hinzu. Weitere Informationen finden Sie unter Vorgehens [Weise beim Hinzufügen von Parametern zu einem Cmdlet-Hilfethema](./how-to-add-parameter-information.md).|
   |`<command:inputTypes>`|Fügt Inhalt für den Abschnitt Eingaben des Hilfe Themas für das Cmdlet hinzu. Weitere Informationen finden Sie unter Vorgehens [Weise beim Hinzufügen von Eingabetypen zu einem Cmdlet-Hilfethema](./how-to-add-input-types-to-a-cmdlet-help-topic.md).|
   |`<command:returnValues>`|Fügt Inhalt für den Abschnitt "Outputs" des Cmdlet-Hilfe Themas hinzu. Weitere Informationen finden Sie unter Vorgehens [Weise beim Hinzufügen von Rückgabe Werten zu einem Cmdlet-Hilfethema](./how-to-add-return-values-to-a-cmdlet-help-topic.md).|
   |`<maml:alertset>`|Fügt dem Abschnitt "Notizen" des Cmdlet-Hilfe Themas Inhalt hinzu. Weitere Informationen finden Sie unter Vorgehens [Weise beim Hinzufügen von Notizen zu einem Cmdlet-Hilfethema](./how-to-add-notes-to-a-cmdlet-help-topic.md).|
   |`<command:examples>`|Fügt Inhalt für den Abschnitt "Beispiele" des Cmdlet-Hilfe Themas hinzu. Weitere Informationen finden Sie unter [Hinzufügen von Beispielen zu einem Cmdlet-Hilfethema](./how-to-add-examples-to-a-cmdlet-help-topic.md).|
   |`<maml:relatedLinks>`|Fügt Inhalt für den Abschnitt "Verwandte Links" des Cmdlet-Hilfe Themas hinzu. Weitere Informationen finden Sie [unter Hinzufügen verwandter Links zu einem Cmdlet-Hilfethema](./how-to-add-related-links-to-a-cmdlet-help-topic.md).|

## <a name="example"></a>Beispiel

 Im folgenden finden Sie ein Beispiel für einen Befehls Knoten, der die Knoten für die verschiedenen Abschnitte des Cmdlet-Hilfe Themas enthält.

```xml
<command:command
  xmlns:maml="https://schemas.microsoft.com/maml/2004/10"
  xmlns:command="https://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="https://schemas.microsoft.com/maml/dev/2004/10">
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

## <a name="see-also"></a>Siehe auch

 [Vorgehensweise beim Hinzufügen des Cmdlet-namens und der Synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [Vorgehensweise beim Hinzufügen der ausführlichen Beschreibung zu einem Cmdlet-Hilfethema](./how-to-add-a-cmdlet-description.md)

 [Vorgehensweise beim Hinzufügen von Syntax zu einem Cmdlet-Hilfethema](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Vorgehensweise beim Hinzufügen von Parametern zu einem Cmdlet-Hilfethema](./how-to-add-parameter-information.md)

 [Vorgehensweise beim Hinzufügen von Eingabetypen zu einem Cmdlet-Hilfethema](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Vorgehensweise beim Hinzufügen von Rückgabe Werten zu einem Cmdlet-Hilfethema](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Vorgehensweise beim Hinzufügen von Notizen zu einem Cmdlet-Hilfethema](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Vorgehensweise beim Hinzufügen von Beispielen zu einem Cmdlet-Hilfethema](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Hinzufügen verwandter Links zu einem Cmdlet-Hilfethema](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)