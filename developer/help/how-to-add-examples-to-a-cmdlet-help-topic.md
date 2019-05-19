---
title: Beispiele für ein Cmdlet-Hilfethema hinzufügen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: b6f8aef76a5f4b5dc1a60425541856ead9a9c77a
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65855113"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a><span data-ttu-id="92374-102">Hinzufügen von Beispielen zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="92374-102">How to Add Examples to a Cmdlet Help Topic</span></span>

## <a name="things-to-know-about-examples-in-cmdlet-help"></a><span data-ttu-id="92374-103">Wichtige Informationen zu Beispielen, in der Cmdlet-Hilfe</span><span class="sxs-lookup"><span data-stu-id="92374-103">Things to Know about Examples in Cmdlet Help</span></span>

- <span data-ttu-id="92374-104">Listen Sie alle Parameternamen in den Befehl aus, selbst wenn die Namen der Parameter optional sind.</span><span class="sxs-lookup"><span data-stu-id="92374-104">List all of the parameter names in the command, even when the parameter names are optional.</span></span> <span data-ttu-id="92374-105">Dadurch wird den Benutzer den Befehl einfach zu interpretieren.</span><span class="sxs-lookup"><span data-stu-id="92374-105">This helps the user to interpret the command easily.</span></span>

- <span data-ttu-id="92374-106">Vermeiden Sie Aliase und partielle Parameternamen, obwohl sie in Windows PowerShell® funktionieren.</span><span class="sxs-lookup"><span data-stu-id="92374-106">Avoid aliases and partial parameter names, even though they work in Windows PowerShell®.</span></span>

- <span data-ttu-id="92374-107">In der Beschreibung zu Beispiel erläutert, die rationale für die Konstruktion des Befehls.</span><span class="sxs-lookup"><span data-stu-id="92374-107">In the example description, explain the rational for the construction of the command.</span></span> <span data-ttu-id="92374-108">Erläutern Sie, warum Sie bestimmte Parameter und Werte ausgewählt haben, und wie Sie Variablen verwenden.</span><span class="sxs-lookup"><span data-stu-id="92374-108">Explain why you chose particular parameters and values, and how you use variables.</span></span>

- <span data-ttu-id="92374-109">Wenn der Befehl Ausdrücke verwendet, wird diese im Detail erläutert.</span><span class="sxs-lookup"><span data-stu-id="92374-109">If the command uses expressions, explain them in detail.</span></span>

- <span data-ttu-id="92374-110">Wenn der Befehl verwendet die Eigenschaften und Methoden der Objekte, insbesondere die Eigenschaften, die nicht in der Standardanzeige angezeigt werden anhand des Beispiels, wie die Gelegenheit dem Benutzer mitgeteilt, über das Objekt.</span><span class="sxs-lookup"><span data-stu-id="92374-110">If the command uses properties and methods of objects, especially properties that do not appear in the default display, use the example as an opportunity tell the user about the object.</span></span>

## <a name="help-views-that-display-examples"></a><span data-ttu-id="92374-111">Hilfeansichten, die Beispiele anzeigen</span><span class="sxs-lookup"><span data-stu-id="92374-111">Help Views that Display Examples</span></span>

<span data-ttu-id="92374-112">Beispiele, die nur in den Ansichten "ausführlich" und "vollständig" der Cmdlet-Hilfe angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="92374-112">Examples appear only in the Detailed and Full views of cmdlet Help.</span></span>

## <a name="adding-an-examples-node"></a><span data-ttu-id="92374-113">Hinzufügen eines Knotens Beispiele</span><span class="sxs-lookup"><span data-stu-id="92374-113">Adding an Examples Node</span></span>

<span data-ttu-id="92374-114">Das folgende XML zeigt, wie einen Beispielen-Knoten hinzugefügt, der einen einzelnen Beispiel-Knoten enthält.</span><span class="sxs-lookup"><span data-stu-id="92374-114">The following XML shows how to add an Examples node that contains a single Example node.</span></span> <span data-ttu-id="92374-115">Fügen Sie zusätzliches Beispiel-Knoten für die einzelnen Beispiele, die Sie im Thema einschließen möchten.</span><span class="sxs-lookup"><span data-stu-id="92374-115">Add additional example nodes for each examples you want to include in the topic.</span></span>

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a><span data-ttu-id="92374-116">Einen Titel hinzufügen</span><span class="sxs-lookup"><span data-stu-id="92374-116">Adding an Example Title</span></span>

<span data-ttu-id="92374-117">Das folgende XML zeigt, wie Sie einen Titel für das Beispiel hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="92374-117">The following XML shows how to add a title for the example.</span></span> <span data-ttu-id="92374-118">Der Titel ist, legen Sie das Beispiel abgesehen von den anderen Beispielen verwendet.</span><span class="sxs-lookup"><span data-stu-id="92374-118">The title is used to set the example apart from other examples.</span></span> <span data-ttu-id="92374-119">Windows PowerShell® verwendet einen Standardheader, der eine sequenzielle Beispielnummer enthält.</span><span class="sxs-lookup"><span data-stu-id="92374-119">Windows PowerShell® uses a standard header that includes a sequential example number.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a><span data-ttu-id="92374-120">Hinzufügen von vorhergehenden Zeichen</span><span class="sxs-lookup"><span data-stu-id="92374-120">Adding Preceding Characters</span></span>

<span data-ttu-id="92374-121">Das folgende XML zeigt, wie Sie Zeichen, z. B. der Windows PowerShell-Eingabeaufforderung hinzufügen, die unmittelbar vor der Befehl im Beispiel (ohne Leerzeichen) angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="92374-121">The following XML shows how to add characters, such as the Windows PowerShell prompt, that are displayed immediately before the example command (without any intervening spaces).</span></span> <span data-ttu-id="92374-122">Windows PowerShell® verwendet die Windows PowerShell-Eingabeaufforderung: C:\PS>.</span><span class="sxs-lookup"><span data-stu-id="92374-122">Windows PowerShell® uses the Windows PowerShell prompt: C:\PS>.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
</command:example>
</command:examples>
```

## <a name="adding-the-command"></a><span data-ttu-id="92374-123">Der Befehl hinzufügen</span><span class="sxs-lookup"><span data-stu-id="92374-123">Adding the Command</span></span>

<span data-ttu-id="92374-124">Das folgende XML zeigt, wie den eigentlichen Befehl, der im Beispiel hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="92374-124">The following XML shows how to add the actual command of the example.</span></span> <span data-ttu-id="92374-125">Wenn Sie den Befehl hinzufügen möchten, geben Sie den gesamten Namen (Alias nicht verwenden) des-Cmdlets und Parameter.</span><span class="sxs-lookup"><span data-stu-id="92374-125">When adding the command, type the entire name (do not use alias) of cmdlets and parameters.</span></span> <span data-ttu-id="92374-126">Außerdem verwenden Sie Kleinbuchstaben, wann immer möglich.</span><span class="sxs-lookup"><span data-stu-id="92374-126">Also, use lowercase characters whenever possible.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
</command:example>
</command:examples>
```

## <a name="adding-a-description"></a><span data-ttu-id="92374-127">Hinzufügen einer Beschreibung</span><span class="sxs-lookup"><span data-stu-id="92374-127">Adding a Description</span></span>

<span data-ttu-id="92374-128">Das folgende XML zeigt, wie Sie eine Beschreibung für das Beispiel hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="92374-128">The following XML shows how to add a description for the example.</span></span> <span data-ttu-id="92374-129">Windows PowerShell® verwendet einen einzigen Satz von \<maml: para >-Tags für die Beschreibung, obwohl mehrere \<maml: para > Tags können verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="92374-129">Windows PowerShell® uses a single set of \<maml:para> tags for the description, even though multiple \<maml:para> tags can be used.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
    </dev:remarks>
</command:example>
</command:examples>
```

## <a name="adding-example-output"></a><span data-ttu-id="92374-130">Beispiel der Ausgabe hinzufügen</span><span class="sxs-lookup"><span data-stu-id="92374-130">Adding Example Output</span></span>

<span data-ttu-id="92374-131">Das folgende XML zeigt, wie Sie die Ausgabe des Befehls hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="92374-131">The following XML shows how to add the output of the command.</span></span> <span data-ttu-id="92374-132">Die Ergebnisse Befehlsinformationen ist optional, aber in einigen Fällen ist es hilfreich sein, den Effekt des anhand bestimmter Parameter veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="92374-132">The command results information is optional, but in some cases it is helpful to demonstrate the effect of using specific parameters.</span></span> <span data-ttu-id="92374-133">Windows PowerShell® anhand von zwei Leerzeichen \<maml: para > Tags aus, um die Ausgabe des Befehls von dem Befehl zu trennen.</span><span class="sxs-lookup"><span data-stu-id="92374-133">Windows PowerShell® uses two sets of blank \<maml:para> tags to separate the command output from the command.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
      <maml:para></maml:para>
      <maml:para></maml:para>
      <maml:para> command output </maml:para>
</dev:remarks>
</command:example>
</command:examples>
```