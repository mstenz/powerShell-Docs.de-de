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
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a><span data-ttu-id="7b2a1-102">Hinzufügen von Eingabetypen zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="7b2a1-102">How to Add Input Types to a Cmdlet Help Topic</span></span>

<span data-ttu-id="7b2a1-103">In diesem Abschnitt wird beschrieben, wie Sie einem Hilfethema für PowerShell-Cmdlets einen Abschnitt **Eingaben** hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="7b2a1-103">This section describes how to add an **INPUTS** section to a PowerShell cmdlet Help topic.</span></span> <span data-ttu-id="7b2a1-104">Im Abschnitt **Eingaben** werden die .NET-Klassen von Objekten aufgelistet, die das Cmdlet als Eingabe aus der Pipeline akzeptiert, entweder nach Wert oder nach Eigenschaftsnamen.</span><span class="sxs-lookup"><span data-stu-id="7b2a1-104">The **INPUTS** section lists the .NET classes of objects that the cmdlet accepts as input from the pipeline, either by value or by property name.</span></span>

<span data-ttu-id="7b2a1-105">Es gibt keine Beschränkung für die Anzahl der Klassen, die Sie einem Abschnitt **Eingaben** hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="7b2a1-105">There is no limit to the number of classes that you can add to an **INPUTS** section.</span></span> <span data-ttu-id="7b2a1-106">Die Eingabetypen sind in einen- `<command:inputTypes>` Knoten eingeschlossen, wobei jede Klasse in ein-Element eingeschlossen ist `<command:inputType>` .</span><span class="sxs-lookup"><span data-stu-id="7b2a1-106">The input types are enclosed in a `<command:inputTypes>` node, with each class enclosed in a `<command:inputType>` element.</span></span>

<span data-ttu-id="7b2a1-107">Das Schema enthält zwei- `<maml:description>` Elemente in jedem- `<command:inputType>` Element.</span><span class="sxs-lookup"><span data-stu-id="7b2a1-107">The schema includes two `<maml:description>` elements in each `<command:inputType>` element.</span></span>
<span data-ttu-id="7b2a1-108">Das- `Get-Help` Cmdlet zeigt jedoch nur den Inhalt des- `<command:inputType>/<maml:description>` Elements an.</span><span class="sxs-lookup"><span data-stu-id="7b2a1-108">However, the `Get-Help` cmdlet displays only the content of the `<command:inputType>/<maml:description>` element.</span></span>

<span data-ttu-id="7b2a1-109">Ab PowerShell 3,0 `Get-Help` zeigt das Cmdlet den Inhalt des-Elements an `<maml:uri>` .</span><span class="sxs-lookup"><span data-stu-id="7b2a1-109">Beginning in PowerShell 3.0, the `Get-Help` cmdlet displays the content of the `<maml:uri>` element.</span></span>
<span data-ttu-id="7b2a1-110">Mit diesem Element können Sie Benutzer an Themen weiterleiten, in denen die .NET-Klasse beschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="7b2a1-110">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="7b2a1-111">Der folgende XML-Code zeigt den- `<maml:inputTypes>` Knoten.</span><span class="sxs-lookup"><span data-stu-id="7b2a1-111">The following XML shows the `<maml:inputTypes>` node.</span></span>

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

<span data-ttu-id="7b2a1-112">Der folgende XML-Code zeigt ein Beispiel für die Verwendung des- `<maml:inputTypes>` Knotens zum Dokumentieren eines Eingabe Typs.</span><span class="sxs-lookup"><span data-stu-id="7b2a1-112">The following XML shows an example of using the `<maml:inputTypes>` node to document an input type.</span></span>

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
