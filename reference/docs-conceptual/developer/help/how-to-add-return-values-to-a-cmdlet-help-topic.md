---
title: Vorgehensweise beim Hinzufügen von Rückgabe Werten zu einem Cmdlet-Hilfethema | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52ab737-753c-4d04-8af7-758d5c805e18
caps.latest.revision: 7
ms.openlocfilehash: a5618b72827d8ef70201437c4a99ea8bf68cdfd3
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83565542"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a>Hinzufügen von Rückgabewerten zu einem Cmdlet-Hilfethema

In diesem Abschnitt wird beschrieben, wie Sie einen Ausgabe Abschnitt zu einem Windows PowerShell-® Cmdlet-Hilfethema hinzufügen. Im Abschnitt "Outputs" werden die .NET-Klassen von Objekten aufgelistet, die vom Cmdlet zurückgegeben oder an die Pipeline übergeben werden.

Es gibt keine Beschränkung für die Anzahl der Klassen, die Sie dem Ausgabe Abschnitt hinzufügen können. Die Rückgabe Typen eines Cmdlets werden in einen Befehl eingefügt \< : returnvalues> Knoten, wobei jede Klasse in einen Befehl eingefügt wird \< : returnValue> Element.

Wenn ein Cmdlet keine Ausgabe generiert, verwenden Sie diesen Abschnitt, um anzugeben, dass keine Ausgabe vorhanden ist. Schreiben Sie z. b. anstelle des Klassen namens "None", und stellen Sie eine kurze Erläuterung bereit. Wenn das Cmdlet die Ausgabe bedingt generiert, verwenden Sie diesen Knoten, um die Bedingungen zu erläutern und die bedingte Ausgabe zu beschreiben.

Das Schema enthält zwei \< MAML: Description>-Elemente in jedem \< Befehl: returnValue> Element. Das `Get-Help` Cmdlet zeigt jedoch nur den Inhalt des Befehls an \< : returnValue>/ \< MAML: Description> Element.

Ab Windows PowerShell 3,0 `Get-Help` zeigt das Cmdlet den Inhalt des \<> Elements MAML: URI an. Mit diesem Element können Sie Benutzer an Themen weiterleiten, in denen die .NET-Klasse beschrieben wird.

Der folgende XML-Code zeigt den \< Knoten MAML: returnvalues>.

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

Der folgende XML-Code zeigt ein Beispiel für die Verwendung des \< Knotens MAML: returnvalues>, um einen Ausgabetyp zu dokumentieren.

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  https://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Get-Date returns a DateTime object. <maml:para>
    </maml:description>
  </command: returnValue>
</command: returnValues>
```
