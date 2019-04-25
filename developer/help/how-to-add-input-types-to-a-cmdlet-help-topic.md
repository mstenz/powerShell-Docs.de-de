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
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a><span data-ttu-id="cad0f-102">Hinzufügen von Eingabetypen zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="cad0f-102">How to Add Input Types to a Cmdlet Help Topic</span></span>

<span data-ttu-id="cad0f-103">In diesem Abschnitt wird beschrieben, wie ein Cmdlet-Hilfethemas Windows PowerShell® einen Abschnitt EINGABEN hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="cad0f-103">This section describes how to add an INPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="cad0f-104">Die EINGABEN Abschnitt listet die .NET Klassen von Objekten, die das Cmdlet als Eingabe aus der Pipeline als Wert oder nach Eigenschaftsname akzeptiert.</span><span class="sxs-lookup"><span data-stu-id="cad0f-104">The INPUTS section lists the .NET classes of objects that the cmdlet accepts as input from the pipeline, either by value or by property name.</span></span>

<span data-ttu-id="cad0f-105">Es gibt keine Beschränkung der Anzahl von Klassen, die einen Abschnitt EINGABEN hinzugefügt werden können.</span><span class="sxs-lookup"><span data-stu-id="cad0f-105">There is no limit to the number of classes that you can add to an INPUTS section.</span></span> <span data-ttu-id="cad0f-106">Die Eingabetypen in eingeschlossen sind ein \<-Befehl: InputTypes > Knoten, bei dem jede Klasse eingeschlossen in einer \<-Befehl: InputType > Element.</span><span class="sxs-lookup"><span data-stu-id="cad0f-106">The input types are enclosed in a \<command:inputTypes> node, with each class enclosed in a  \<command:inputType> element.</span></span>

<span data-ttu-id="cad0f-107">Das Schema enthält zwei \<Maml:description >-Elemente in jeder \<-Befehl: InputType > Element.</span><span class="sxs-lookup"><span data-stu-id="cad0f-107">The schema includes two \<maml:description> elements in each \<command:inputType> element.</span></span> <span data-ttu-id="cad0f-108">Allerdings die `Get-Help` Cmdlet zeigt nur den Inhalt der \<-Befehl: InputType > /\<Maml:description >) Element.</span><span class="sxs-lookup"><span data-stu-id="cad0f-108">However, the `Get-Help` cmdlet displays only the content of the \<command:inputType>/\<maml:description>) element.</span></span>

<span data-ttu-id="cad0f-109">Ab Windows PowerShell 3.0 wird das `Get-Help` Cmdlet zeigt den Inhalt der \<maml: URI > Element.</span><span class="sxs-lookup"><span data-stu-id="cad0f-109">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="cad0f-110">Dieses Element können Sie die Benutzer zu Themen zu erhalten, die die Klasse .NET beschreiben.</span><span class="sxs-lookup"><span data-stu-id="cad0f-110">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="cad0f-111">Das folgende XML zeigt die \<Maml:inputTypes > Knoten.</span><span class="sxs-lookup"><span data-stu-id="cad0f-111">The following XML shows the \<maml:inputTypes> node.</span></span>

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

<span data-ttu-id="cad0f-112">Das folgende XML zeigt ein Beispiel der Verwendung der \<Maml:inputTypes > Knoten aus, um einen Eingabetyp zu dokumentieren.</span><span class="sxs-lookup"><span data-stu-id="cad0f-112">The following XML shows an example of using the \<maml:inputTypes> node to document an input type.</span></span>

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