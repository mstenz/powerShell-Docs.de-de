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
ms.openlocfilehash: b5a5f3e187634b38ba3ce3da18a7ad64ccc09ce2
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893015"
---
# <a name="how-to-create-the-cmdlet-help-file"></a>Erstellen der Cmdlet-Hilfedatei

In diesem Abschnitt wird beschrieben, wie Sie eine gültige XML-Datei erstellen, die Inhalt für Windows PowerShell-Cmdlet-Hilfe Themen enthält. In diesem Abschnitt wird erläutert, wie Sie die Hilfedatei benennen, die entsprechenden XML-Header hinzufügen und Knoten hinzufügen, die die verschiedenen Abschnitte der Cmdlet-Hilfe Inhalte enthalten.

> [!NOTE]
> Eine umfassende Ansicht einer Hilfedatei erhalten Sie, indem Sie eine der `dll-Help.xml` Dateien öffnen, die sich im Windows PowerShell-Installationsverzeichnis befinden. Die `Microsoft.PowerShell.Commands.Management.dll-Help.xml` Datei enthält z. b. Inhalte für mehrere PowerShell-Cmdlets.

### <a name="how-to-create-a-cmdlet-help-file"></a>Erstellen einer Cmdlet-Hilfedatei

1. Erstellen Sie eine Textdatei, und speichern Sie Sie mithilfe der UTF8-Codierung. Der Dateiname muss das folgende Format aufweisen, damit Windows PowerShell ihn als Cmdlet-Hilfedatei erkennen kann.

   `<PSSnapInAssemblyName>.dll-Help.xml`

1. Fügen Sie die folgenden XML-Header der Textdatei hinzu. Beachten Sie, dass die Datei mit dem Schema der Microsoft-Unterstützung Markup Sprache (MAML) überprüft wird. PowerShell stellt derzeit keine Tools zum Überprüfen der Datei bereit.

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

1. Fügen Sie der Cmdlet-Hilfedatei einen **Befehls** Knoten für jedes Cmdlet in der Assembly hinzu. Jeder Knoten im **Befehls** Knoten bezieht sich auf die verschiedenen Abschnitte des Cmdlet-Hilfe Themas.

   In der folgenden Tabelle wird das XML-Element für jeden Knoten aufgeführt, gefolgt von einer Beschreibung der einzelnen Knoten.

   |           Node           |                                                                                                     Beschreibung                                                                                                     |
   | ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | `<details>`              | Fügt Inhalt für die Abschnitte "Name" und "Synopsis" des Cmdlet-Hilfe Themas hinzu. Weitere Informationen finden Sie unter Vorgehens [Weise beim Hinzufügen des Cmdlet-namens und der Synchronisierungs](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)Datei. |
   | `<maml:description>`     | Fügt Inhalt für den Beschreibungs Abschnitt des Cmdlet-Hilfe Themas hinzu. Weitere Informationen finden Sie unter Vorgehens [Weise beim Hinzufügen der ausführlichen Beschreibung zu einem Cmdlet-Hilfethema](./how-to-add-a-cmdlet-description.md).                    |
   | `<command:syntax>`       | Fügt Inhalt für den Syntax Abschnitt des Cmdlet-Hilfe Themas hinzu. Weitere Informationen finden Sie unter Vorgehens [Weise beim Hinzufügen von Syntax zu einem Cmdlet-Hilfethema](./how-to-add-syntax-to-a-cmdlet-help-topic.md).                                  |
   | `<command:parameters>`   | Fügt Inhalt für den Parameter Abschnitt des Cmdlet-Hilfe Themas hinzu. Weitere Informationen finden Sie unter Vorgehens [Weise beim Hinzufügen von Parametern zu einem Cmdlet-Hilfethema](./how-to-add-parameter-information.md).                                  |
   | `<command:inputTypes>`   | Fügt Inhalt für den Abschnitt Eingaben des Hilfe Themas für das Cmdlet hinzu. Weitere Informationen finden Sie unter Vorgehens [Weise beim Hinzufügen von Eingabetypen zu einem Cmdlet-Hilfethema](./how-to-add-input-types-to-a-cmdlet-help-topic.md).                        |
   | `<command:returnValues>` | Fügt Inhalt für den Abschnitt "Outputs" des Cmdlet-Hilfe Themas hinzu. Weitere Informationen finden Sie unter Vorgehens [Weise beim Hinzufügen von Rückgabe Werten zu einem Cmdlet-Hilfethema](./how-to-add-return-values-to-a-cmdlet-help-topic.md).                   |
   | `<maml:alertset>`        | Fügt Inhalt für den Abschnitt Notizen des Cmdlet-Hilfe Themas hinzu. Weitere Informationen finden Sie unter Vorgehens [Weise beim Hinzufügen von Notizen zu einem Cmdlet-Hilfethema](./how-to-add-notes-to-a-cmdlet-help-topic.md).                                      |
   | `<command:examples>`     | Fügt Inhalt für den Abschnitt "Beispiele" des Cmdlet-Hilfe Themas hinzu. Weitere Informationen finden Sie unter [Hinzufügen von Beispielen zu einem Cmdlet-Hilfethema](./how-to-add-examples-to-a-cmdlet-help-topic.md).                            |
   | `<maml:relatedLinks>`    | Fügt Inhalt für den Abschnitt "Verwandte Links" des Cmdlet-Hilfe Themas hinzu. Weitere Informationen finden Sie [unter Hinzufügen verwandter Links zu einem Cmdlet-Hilfethema](./how-to-add-related-links-to-a-cmdlet-help-topic.md).             |

## <a name="example"></a>Beispiel

 Im folgenden finden Sie ein Beispiel für einen **Befehls** Knoten, der die Knoten für die verschiedenen Abschnitte des Cmdlet-Hilfe Themas enthält.

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

## <a name="see-also"></a>Weitere Informationen

 [Vorgehensweise beim Hinzufügen des Cmdlet-namens und der Synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [Vorgehensweise beim Hinzufügen der ausführlichen Beschreibung zu einem Cmdlet-Hilfethema](./how-to-add-a-cmdlet-description.md)

 [Hinzufügen einer Syntax zu einem Cmdlet-Hilfethema](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [Vorgehensweise beim Hinzufügen von Parametern zu einem Cmdlet-Hilfethema](./how-to-add-parameter-information.md)

 [Hinzufügen von Eingabetypen zu einem Cmdlet-Hilfethema](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [Hinzufügen von Rückgabewerten zu einem Cmdlet-Hilfethema](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [Vorgehensweise beim Hinzufügen von Notizen zu einem Cmdlet-Hilfethema](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [Hinzufügen von Beispielen zu einem Cmdlet-Hilfethema](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [Hinzufügen von zugehörigen Verknüpfungen zu einem Cmdlet-Hilfethema](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [Windows PowerShell SDK](../windows-powershell-reference.md)
