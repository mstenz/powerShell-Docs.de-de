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
ms.openlocfilehash: 37af16d0279b6487c78f90eb19bcfe5c152ed9e7
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/04/2020
ms.locfileid: "76996052"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a>Hinzufügen von Eingabetypen zu einem Cmdlet-Hilfethema

In diesem Abschnitt wird beschrieben, wie Sie einem Windows PowerShell-® Cmdlet-Hilfethema einen Abschnitt Eingaben hinzufügen. Im Abschnitt Eingaben werden die .NET-Klassen von Objekten aufgelistet, die das Cmdlet als Eingabe aus der Pipeline akzeptiert, entweder nach Wert oder nach Eigenschaftsnamen.

Es gibt keine Beschränkung für die Anzahl der Klassen, die Sie einem Abschnitt Eingaben hinzufügen können. Die Eingabetypen sind in einem \<Befehl enthalten: InputTypes > Knoten, wobei jede Klasse in einen \<Befehl eingeschlossen ist: InputType > Element.

Das Schema enthält zwei \<MAML: Description > Elemente in jedem \<Befehl: InputType > Element. Das `Get-Help`-Cmdlet zeigt jedoch nur den Inhalt des \<Befehls: InputType >/\<MAML: Description >)-Element an.

Ab Windows PowerShell 3,0 zeigt das Cmdlet "`Get-Help`" den Inhalt des > Elements \<MAML: URI an. Mit diesem Element können Sie Benutzer an Themen weiterleiten, in denen die .NET-Klasse beschrieben wird.

Der folgende XML-Code zeigt den Knoten \<MAML: InputTypes >.

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

Der folgende XML-Code zeigt ein Beispiel für die Verwendung des Knotens \<MAML: InputTypes >, um einen Eingabetyp zu dokumentieren.

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  https://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> You can pipe a date to the Set-Date cmdlet. <maml:para>
    <maml:description>
  </command:inputType>
</command:inputTypes>
```