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
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a><span data-ttu-id="769f6-102">Hinzufügen von Rückgabewerten zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="769f6-102">How to Add Return Values to a Cmdlet Help Topic</span></span>

<span data-ttu-id="769f6-103">In diesem Abschnitt wird beschrieben, wie ein Cmdlet-Hilfethemas Windows PowerShell® einen Abschnitt "OUTPUTS" hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="769f6-103">This section describes how to add an OUTPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="769f6-104">Der Abschnitt "OUTPUTS" enthält, die .NET-Klassen von Objekten, die das Cmdlet gibt zurück oder über die Pipeline übergeben, wird.</span><span class="sxs-lookup"><span data-stu-id="769f6-104">The OUTPUTS section lists the .NET classes of objects that the cmdlet returns or passes down the pipeline.</span></span>

<span data-ttu-id="769f6-105">Es gibt keine Beschränkung der Anzahl von Klassen, die Sie den Abschnitt "OUTPUTS" hinzugefügt werden können.</span><span class="sxs-lookup"><span data-stu-id="769f6-105">There is no limit to the number of classes that you can add to the OUTPUTS section.</span></span> <span data-ttu-id="769f6-106">Die Rückgabetypen eines Cmdlets in eingeschlossen sind ein \<-Befehl: ReturnValues > Knoten, bei dem jede Klasse eingeschlossen in einer \<-Befehl: ReturnValue > Element.</span><span class="sxs-lookup"><span data-stu-id="769f6-106">The return types of a cmdlet are enclosed in a \<command:returnValues> node, with each class enclosed in a \<command:returnValue> element.</span></span>

<span data-ttu-id="769f6-107">Wenn ein Cmdlet keine Ausgabe generiert wird, verwenden Sie diesen Abschnitt, um anzugeben, dass keine Ausgabe.</span><span class="sxs-lookup"><span data-stu-id="769f6-107">If a cmdlet does not generate any output, use this section to indicate that there is no output.</span></span> <span data-ttu-id="769f6-108">Beispielsweise anstelle der Klassennamen schreiben Sie "None", und geben Sie eine kurze Erläuterung.</span><span class="sxs-lookup"><span data-stu-id="769f6-108">For example, in place of the class name, write "None" and provide a brief explanation.</span></span> <span data-ttu-id="769f6-109">Wenn das Cmdlet bedingt Ausgabe generiert wird, verwenden Sie diesen Knoten, die Bedingungen und außerdem wird beschrieben, die bedingten Ausgabe.</span><span class="sxs-lookup"><span data-stu-id="769f6-109">If the cmdlet generates output conditionally, use this node to explain the conditions and describe the conditional output.</span></span>

<span data-ttu-id="769f6-110">Das Schema enthält zwei \<Maml:description >-Elemente in jeder \<-Befehl: ReturnValue > Element.</span><span class="sxs-lookup"><span data-stu-id="769f6-110">The schema includes two \<maml:description> elements in each \<command:returnValue> element.</span></span> <span data-ttu-id="769f6-111">Allerdings die `Get-Help` Cmdlet zeigt nur den Inhalt der \<-Befehl: ReturnValue > /\<Maml:description > Element.</span><span class="sxs-lookup"><span data-stu-id="769f6-111">However, the `Get-Help` cmdlet displays only the content of the \<command:returnValue>/\<maml:description> element.</span></span>

<span data-ttu-id="769f6-112">Ab Windows PowerShell 3.0 wird das `Get-Help` Cmdlet zeigt den Inhalt der \<maml: URI > Element.</span><span class="sxs-lookup"><span data-stu-id="769f6-112">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="769f6-113">Dieses Element können Sie die Benutzer zu Themen zu erhalten, die die Klasse .NET beschreiben.</span><span class="sxs-lookup"><span data-stu-id="769f6-113">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="769f6-114">Das folgende XML zeigt die \<Maml:returnValues > Knoten.</span><span class="sxs-lookup"><span data-stu-id="769f6-114">The following XML shows the \<maml:returnValues> node.</span></span>

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

<span data-ttu-id="769f6-115">Das folgende XML zeigt ein Beispiel der Verwendung der \<Maml:returnValues > Knoten aus, um einen Ausgabetyp zu dokumentieren.</span><span class="sxs-lookup"><span data-stu-id="769f6-115">The following XML shows an example of using the \<maml:returnValues> node to document an output type.</span></span>

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



