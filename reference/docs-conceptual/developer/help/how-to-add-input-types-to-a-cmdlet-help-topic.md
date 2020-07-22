---
title: Hinzufügen von Eingabetypen zu einem Cmdlet-Hilfethema
ms.date: 09/12/2016
ms.openlocfilehash: d41c49ff48cf361c2ba694d11576e84a9367eef5
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893423"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a>Hinzufügen von Eingabetypen zu einem Cmdlet-Hilfethema

In diesem Abschnitt wird beschrieben, wie Sie einem Hilfethema für PowerShell-Cmdlets einen Abschnitt **Eingaben** hinzufügen. Im Abschnitt **Eingaben** werden die .NET-Klassen von Objekten aufgelistet, die das Cmdlet als Eingabe aus der Pipeline akzeptiert, entweder nach Wert oder nach Eigenschaftsnamen.

Es gibt keine Beschränkung für die Anzahl der Klassen, die Sie einem Abschnitt **Eingaben** hinzufügen können. Die Eingabetypen sind in einen- `<command:inputTypes>` Knoten eingeschlossen, wobei jede Klasse in ein-Element eingeschlossen ist `<command:inputType>` .

Das Schema enthält zwei- `<maml:description>` Elemente in jedem- `<command:inputType>` Element.
Das- `Get-Help` Cmdlet zeigt jedoch nur den Inhalt des- `<command:inputType>/<maml:description>` Elements an.

Ab PowerShell 3,0 `Get-Help` zeigt das Cmdlet den Inhalt des-Elements an `<maml:uri>` .
Mit diesem Element können Sie Benutzer an Themen weiterleiten, in denen die .NET-Klasse beschrieben wird.

Der folgende XML-Code zeigt den- `<maml:inputTypes>` Knoten.

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

Der folgende XML-Code zeigt ein Beispiel für die Verwendung des- `<maml:inputTypes>` Knotens zum Dokumentieren eines Eingabe Typs.

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
