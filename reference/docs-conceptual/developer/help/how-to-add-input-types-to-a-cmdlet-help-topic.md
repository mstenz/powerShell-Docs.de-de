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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361239"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a><span data-ttu-id="29c6b-102">Hinzufügen von Eingabetypen zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="29c6b-102">How to Add Input Types to a Cmdlet Help Topic</span></span>

<span data-ttu-id="29c6b-103">In diesem Abschnitt wird beschrieben, wie Sie einem Windows PowerShell-® Cmdlet-Hilfethema einen Abschnitt Eingaben hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="29c6b-103">This section describes how to add an INPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="29c6b-104">Im Abschnitt Eingaben werden die .NET-Klassen von Objekten aufgelistet, die das Cmdlet als Eingabe aus der Pipeline akzeptiert, entweder nach Wert oder nach Eigenschaftsnamen.</span><span class="sxs-lookup"><span data-stu-id="29c6b-104">The INPUTS section lists the .NET classes of objects that the cmdlet accepts as input from the pipeline, either by value or by property name.</span></span>

<span data-ttu-id="29c6b-105">Es gibt keine Beschränkung für die Anzahl der Klassen, die Sie einem Abschnitt Eingaben hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="29c6b-105">There is no limit to the number of classes that you can add to an INPUTS section.</span></span> <span data-ttu-id="29c6b-106">Die Eingabetypen sind in einem \<Befehl enthalten: InputTypes > Knoten, wobei jede Klasse in einen \<Befehl eingeschlossen ist: InputType > Element.</span><span class="sxs-lookup"><span data-stu-id="29c6b-106">The input types are enclosed in a \<command:inputTypes> node, with each class enclosed in a  \<command:inputType> element.</span></span>

<span data-ttu-id="29c6b-107">Das Schema enthält zwei \<MAML: Description > Elemente in jedem \<Befehl: InputType > Element.</span><span class="sxs-lookup"><span data-stu-id="29c6b-107">The schema includes two \<maml:description> elements in each \<command:inputType> element.</span></span> <span data-ttu-id="29c6b-108">Das `Get-Help`-Cmdlet zeigt jedoch nur den Inhalt des \<Befehls: InputType >/\<MAML: Description >)-Element an.</span><span class="sxs-lookup"><span data-stu-id="29c6b-108">However, the `Get-Help` cmdlet displays only the content of the \<command:inputType>/\<maml:description>) element.</span></span>

<span data-ttu-id="29c6b-109">Ab Windows PowerShell 3,0 zeigt das Cmdlet "`Get-Help`" den Inhalt des > Elements \<MAML: URI an.</span><span class="sxs-lookup"><span data-stu-id="29c6b-109">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="29c6b-110">Mit diesem Element können Sie Benutzer an Themen weiterleiten, in denen die .NET-Klasse beschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="29c6b-110">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="29c6b-111">Der folgende XML-Code zeigt den Knoten \<MAML: InputTypes >.</span><span class="sxs-lookup"><span data-stu-id="29c6b-111">The following XML shows the \<maml:inputTypes> node.</span></span>

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

<span data-ttu-id="29c6b-112">Der folgende XML-Code zeigt ein Beispiel für die Verwendung des Knotens \<MAML: InputTypes >, um einen Eingabetyp zu dokumentieren.</span><span class="sxs-lookup"><span data-stu-id="29c6b-112">The following XML shows an example of using the \<maml:inputTypes> node to document an input type.</span></span>

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