---
title: Vorgehensweise beim Hinzufügen von Eingabetypen zu einem Cmdlet-Hilfethema | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 432798e4-5d69-46b1-9517-ff09bffaa4be
caps.latest.revision: 7
ms.openlocfilehash: f213605dda0132051d983f8608515325e815c455
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361239"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a>Hinzufügen von Eingabetypen zu einem Cmdlet-Hilfethema

In diesem Abschnitt wird beschrieben, wie Sie einem Windows PowerShell-® Cmdlet-Hilfethema einen Abschnitt Eingaben hinzufügen. Im Abschnitt Eingaben werden die .NET-Klassen von Objekten aufgelistet, die das Cmdlet als Eingabe aus der Pipeline akzeptiert, entweder nach Wert oder nach Eigenschaftsnamen.

Es gibt keine Beschränkung für die Anzahl der Klassen, die Sie einem Abschnitt Eingaben hinzufügen können. Die Eingabetypen sind in einem \<-Befehl: InputTypes > Knoten eingeschlossen, wobei jede Klasse in ein \<command: InputType >-Element eingeschlossen ist.

Das Schema enthält zwei \<maml: Description > Elemente in jedem \<command: InputType >-Element. Das Cmdlet "`Get-Help`" zeigt jedoch nur den Inhalt des Elements "\<command: InputType >/\<maml: Description >" an.

Ab Windows PowerShell 3,0 zeigt das Cmdlet "`Get-Help`" den Inhalt des > Elements "\<maml: URI" an. Mit diesem Element können Sie Benutzer an Themen weiterleiten, in denen die .NET-Klasse beschrieben wird.

Der folgende XML-Code zeigt den Knoten \<maml: InputTypes >.

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

Der folgende XML-Code zeigt ein Beispiel für die Verwendung des Knotens \<maml: InputTypes >, um einen Eingabetyp zu dokumentieren.

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