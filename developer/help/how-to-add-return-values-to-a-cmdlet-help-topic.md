---
title: So hinzu Return-Werte in einer Cmdlet-Hilfethemas | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52ab737-753c-4d04-8af7-758d5c805e18
caps.latest.revision: 7
ms.openlocfilehash: b21811e5a5a819c3d5c4a55fcbe685a84819b71d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859436"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a>Hinzufügen von Rückgabewerten zu einem Cmdlet-Hilfethema

In diesem Abschnitt wird beschrieben, wie ein Cmdlet-Hilfethemas Windows PowerShell® einen Abschnitt "OUTPUTS" hinzugefügt. Der Abschnitt "OUTPUTS" enthält, die .NET-Klassen von Objekten, die das Cmdlet gibt zurück oder über die Pipeline übergeben, wird.

Es gibt keine Beschränkung der Anzahl von Klassen, die Sie den Abschnitt "OUTPUTS" hinzugefügt werden können. Die Rückgabetypen eines Cmdlets in eingeschlossen sind ein \<-Befehl: ReturnValues > Knoten, bei dem jede Klasse eingeschlossen in einer \<-Befehl: ReturnValue > Element.

Wenn ein Cmdlet keine Ausgabe generiert wird, verwenden Sie diesen Abschnitt, um anzugeben, dass keine Ausgabe. Beispielsweise anstelle der Klassennamen schreiben Sie "None", und geben Sie eine kurze Erläuterung. Wenn das Cmdlet bedingt Ausgabe generiert wird, verwenden Sie diesen Knoten, die Bedingungen und außerdem wird beschrieben, die bedingten Ausgabe.

Das Schema enthält zwei \<Maml:description >-Elemente in jeder \<-Befehl: ReturnValue > Element. Allerdings die `Get-Help` Cmdlet zeigt nur den Inhalt der \<-Befehl: ReturnValue > /\<Maml:description > Element.

Ab Windows PowerShell 3.0 wird das `Get-Help` Cmdlet zeigt den Inhalt der \<maml: URI > Element. Dieses Element können Sie die Benutzer zu Themen zu erhalten, die die Klasse .NET beschreiben.

Das folgende XML zeigt die \<Maml:returnValues > Knoten.

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> Class Name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
       <maml:para> Brief description <maml:para>

</maml:description>
  </command: returnValue>
</command: returnValues>
```

Das folgende XML zeigt ein Beispiel der Verwendung der \<Maml:returnValues > Knoten aus, um einen Ausgabetyp zu dokumentieren.

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Get-Date returns a DateTime object. <maml:para>
    </maml:description>
  </command: returnValue>
</command: returnValues>
```



