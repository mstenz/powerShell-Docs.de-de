---
title: Hinzufügen von Eingabetypen zu einem Cmdlet-Hilfethemas | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 432798e4-5d69-46b1-9517-ff09bffaa4be
caps.latest.revision: 7
ms.openlocfilehash: f213605dda0132051d983f8608515325e815c455
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083432"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a>Hinzufügen von Eingabetypen zu einem Cmdlet-Hilfethema

In diesem Abschnitt wird beschrieben, wie ein Cmdlet-Hilfethemas Windows PowerShell® einen Abschnitt EINGABEN hinzugefügt. Die EINGABEN Abschnitt listet die .NET Klassen von Objekten, die das Cmdlet als Eingabe aus der Pipeline als Wert oder nach Eigenschaftsname akzeptiert.

Es gibt keine Beschränkung der Anzahl von Klassen, die einen Abschnitt EINGABEN hinzugefügt werden können. Die Eingabetypen in eingeschlossen sind ein \<-Befehl: InputTypes > Knoten, bei dem jede Klasse eingeschlossen in einer \<-Befehl: InputType > Element.

Das Schema enthält zwei \<Maml:description >-Elemente in jeder \<-Befehl: InputType > Element. Allerdings die `Get-Help` Cmdlet zeigt nur den Inhalt der \<-Befehl: InputType > /\<Maml:description >) Element.

Ab Windows PowerShell 3.0 wird das `Get-Help` Cmdlet zeigt den Inhalt der \<maml: URI > Element. Dieses Element können Sie die Benutzer zu Themen zu erhalten, die die Klasse .NET beschreiben.

Das folgende XML zeigt die \<Maml:inputTypes > Knoten.

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> Class name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Brief description </maml:para>
    </maml:description>
  </command:inputType>
</command:inputTypes>
```

Das folgende XML zeigt ein Beispiel der Verwendung der \<Maml:inputTypes > Knoten aus, um einen Eingabetyp zu dokumentieren.

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> You can pipe a date to the Set-Date cmdlet. <maml:para>
    <maml:description>
  </command:inputType>
</command:inputTypes>
```