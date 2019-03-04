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
ms.openlocfilehash: 5e8d1df6b423bfd2cd6b0a64a8875dea9c3fb4ef
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857316"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a><span data-ttu-id="08bac-102">Hinzufügen von Beispielen zu einem Cmdlet-Hilfethema</span><span class="sxs-lookup"><span data-stu-id="08bac-102">How to Add Examples to a Cmdlet Help Topic</span></span>

- [<span data-ttu-id="08bac-103">Wichtige Informationen zu Beispielen, in der Cmdlet-Hilfe</span><span class="sxs-lookup"><span data-stu-id="08bac-103">Things to Know about Examples in Cmdlet Help</span></span>](#Things-to-Know-about-Examples-in-Cmdlet-Help)

- [<span data-ttu-id="08bac-104">Hilfeansichten, die Beispiele anzeigen</span><span class="sxs-lookup"><span data-stu-id="08bac-104">Help Views that Display Examples</span></span>](#Help-Views-that-Display-Examples)

- [<span data-ttu-id="08bac-105">Hinzufügen eines Knotens Beispiele</span><span class="sxs-lookup"><span data-stu-id="08bac-105">Adding an Examples Node</span></span>](#Adding-an-Examples-Node)

- [<span data-ttu-id="08bac-106">Hinzufügen von vorhergehenden Zeichen</span><span class="sxs-lookup"><span data-stu-id="08bac-106">Adding Preceding Characters</span></span>](#Adding-Preceding-Characters)

- [<span data-ttu-id="08bac-107">Der Befehl hinzufügen</span><span class="sxs-lookup"><span data-stu-id="08bac-107">Adding the Command</span></span>](#Adding-the-Command)

- [<span data-ttu-id="08bac-108">Hinzufügen einer Beschreibung</span><span class="sxs-lookup"><span data-stu-id="08bac-108">Adding a Description</span></span>](#Adding-a-Description)

- [<span data-ttu-id="08bac-109">Beispiel der Ausgabe hinzufügen</span><span class="sxs-lookup"><span data-stu-id="08bac-109">Adding Example Output</span></span>](#Adding-Example-Output)

## <a name="things-to-know-about-examples-in-cmdlet-help"></a><span data-ttu-id="08bac-110">Wichtige Informationen zu Beispielen, in der Cmdlet-Hilfe</span><span class="sxs-lookup"><span data-stu-id="08bac-110">Things to Know about Examples in Cmdlet Help</span></span>

- <span data-ttu-id="08bac-111">Listen Sie alle Parameternamen in den Befehl aus, selbst wenn die Namen der Parameter optional sind.</span><span class="sxs-lookup"><span data-stu-id="08bac-111">List all of the parameter names in the command, even when the parameter names are optional.</span></span> <span data-ttu-id="08bac-112">Dadurch wird den Benutzer den Befehl einfach zu interpretieren.</span><span class="sxs-lookup"><span data-stu-id="08bac-112">This helps the user to interpret the command easily.</span></span>

- <span data-ttu-id="08bac-113">Vermeiden Sie Aliase und partielle Parameternamen, obwohl sie in Windows PowerShell® funktionieren.</span><span class="sxs-lookup"><span data-stu-id="08bac-113">Avoid aliases and partial parameter names, even though they work in Windows PowerShell®.</span></span>

- <span data-ttu-id="08bac-114">In der Beschreibung zu Beispiel erläutert, die rationale für die Konstruktion des Befehls.</span><span class="sxs-lookup"><span data-stu-id="08bac-114">In the example description, explain the rational for the construction of the command.</span></span> <span data-ttu-id="08bac-115">Erläutern Sie, warum Sie bestimmte Parameter und Werte ausgewählt haben, und wie Sie Variablen verwenden.</span><span class="sxs-lookup"><span data-stu-id="08bac-115">Explain why you chose particular parameters and values, and how you use variables.</span></span>

- <span data-ttu-id="08bac-116">Wenn der Befehl Ausdrücke verwendet, wird diese im Detail erläutert.</span><span class="sxs-lookup"><span data-stu-id="08bac-116">If the command uses expressions, explain them in detail.</span></span>

- <span data-ttu-id="08bac-117">Wenn der Befehl verwendet die Eigenschaften und Methoden der Objekte, insbesondere die Eigenschaften, die nicht in der Standardanzeige angezeigt werden anhand des Beispiels, wie die Gelegenheit dem Benutzer mitgeteilt, über das Objekt.</span><span class="sxs-lookup"><span data-stu-id="08bac-117">If the command uses properties and methods of objects, especially properties that do not appear in the default display, use the example as an opportunity tell the user about the object.</span></span>

## <a name="help-views-that-display-examples"></a><span data-ttu-id="08bac-118">Hilfeansichten, die Beispiele anzeigen</span><span class="sxs-lookup"><span data-stu-id="08bac-118">Help Views that Display Examples</span></span>

<span data-ttu-id="08bac-119">Beispiele, die nur in den Ansichten "ausführlich" und "vollständig" der Cmdlet-Hilfe angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="08bac-119">Examples appear only in the Detailed and Full views of cmdlet Help.</span></span>

## <a name="adding-an-examples-node"></a><span data-ttu-id="08bac-120">Hinzufügen eines Knotens Beispiele</span><span class="sxs-lookup"><span data-stu-id="08bac-120">Adding an Examples Node</span></span>

<span data-ttu-id="08bac-121">Das folgende XML zeigt, wie einen Beispielen-Knoten hinzugefügt, der einen einzelnen Beispiel-Knoten enthält.</span><span class="sxs-lookup"><span data-stu-id="08bac-121">The following XML shows how to add an Examples node that contains a single Example node.</span></span> <span data-ttu-id="08bac-122">Fügen Sie zusätzliches Beispiel-Knoten für die einzelnen Beispiele, die Sie im Thema einschließen möchten.</span><span class="sxs-lookup"><span data-stu-id="08bac-122">Add additional example nodes for each examples you want to include in the topic.</span></span>

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a><span data-ttu-id="08bac-123">Einen Titel hinzufügen</span><span class="sxs-lookup"><span data-stu-id="08bac-123">Adding an Example Title</span></span>

<span data-ttu-id="08bac-124">Das folgende XML zeigt, wie Sie einen Titel für das Beispiel hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="08bac-124">The following XML shows how to add a title for the example.</span></span> <span data-ttu-id="08bac-125">Der Titel ist, legen Sie das Beispiel abgesehen von den anderen Beispielen verwendet.</span><span class="sxs-lookup"><span data-stu-id="08bac-125">The title is used to set the example apart from other examples.</span></span> <span data-ttu-id="08bac-126">Windows PowerShell® verwendet einen Standardheader, der eine sequenzielle Beispielnummer enthält.</span><span class="sxs-lookup"><span data-stu-id="08bac-126">Windows PowerShell® uses a standard header that includes a sequential example number.</span></span>

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a><span data-ttu-id="08bac-127">Hinzufügen von vorhergehenden Zeichen</span><span class="sxs-lookup"><span data-stu-id="08bac-127">Adding Preceding Characters</span></span>

<span data-ttu-id="08bac-128">Das folgende XML zeigt, wie Sie Zeichen, z. B. der Windows PowerShell-Eingabeaufforderung hinzufügen, die unmittelbar vor der Befehl im Beispiel (ohne Leerzeichen) angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="08bac-128">The following XML shows how to add characters, such as the Windows PowerShell prompt, that are displayed immediately before the example command (without any intervening spaces).</span></span> <span data-ttu-id="08bac-129">Windows PowerShell® verwendet die Windows PowerShell-Eingabeaufforderung: C:\PS>.</span><span class="sxs-lookup"><span data-stu-id="08bac-129">Windows PowerShell® uses the Windows PowerShell prompt: C:\PS>.</span></span>

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

## <a name="adding-the-command"></a><span data-ttu-id="08bac-130">Der Befehl hinzufügen</span><span class="sxs-lookup"><span data-stu-id="08bac-130">Adding the Command</span></span>

<span data-ttu-id="08bac-131">Das folgende XML zeigt, wie den eigentlichen Befehl, der im Beispiel hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="08bac-131">The following XML shows how to add the actual command of the example.</span></span> <span data-ttu-id="08bac-132">Wenn Sie den Befehl hinzufügen möchten, geben Sie den gesamten Namen (Alias nicht verwenden) des-Cmdlets und Parameter.</span><span class="sxs-lookup"><span data-stu-id="08bac-132">When adding the command, type the entire name (do not use alias) of cmdlets and parameters.</span></span> <span data-ttu-id="08bac-133">Außerdem verwenden Sie Kleinbuchstaben, wann immer möglich.</span><span class="sxs-lookup"><span data-stu-id="08bac-133">Also, use lowercase characters whenever possible.</span></span>

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

## <a name="adding-a-description"></a><span data-ttu-id="08bac-134">Hinzufügen einer Beschreibung</span><span class="sxs-lookup"><span data-stu-id="08bac-134">Adding a Description</span></span>

<span data-ttu-id="08bac-135">Das folgende XML zeigt, wie Sie eine Beschreibung für das Beispiel hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="08bac-135">The following XML shows how to add a description for the example.</span></span> <span data-ttu-id="08bac-136">Windows PowerShell® verwendet einen einzigen Satz von \<maml: para >-Tags für die Beschreibung, obwohl mehrere \<maml: para > Tags können verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="08bac-136">Windows PowerShell® uses a single set of \<maml:para> tags for the description, even though multiple \<maml:para> tags can be used.</span></span>

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

## <a name="adding-example-output"></a><span data-ttu-id="08bac-137">Beispiel der Ausgabe hinzufügen</span><span class="sxs-lookup"><span data-stu-id="08bac-137">Adding Example Output</span></span>

<span data-ttu-id="08bac-138">Das folgende XML zeigt, wie Sie die Ausgabe des Befehls hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="08bac-138">The following XML shows how to add the output of the command.</span></span> <span data-ttu-id="08bac-139">Die Ergebnisse Befehlsinformationen ist optional, aber in einigen Fällen ist es hilfreich sein, den Effekt des anhand bestimmter Parameter veranschaulichen.</span><span class="sxs-lookup"><span data-stu-id="08bac-139">The command results information is optional, but in some cases it is helpful to demonstrate the effect of using specific parameters.</span></span> <span data-ttu-id="08bac-140">Windows PowerShell® anhand von zwei Leerzeichen \<maml: para > Tags aus, um die Ausgabe des Befehls von dem Befehl zu trennen.</span><span class="sxs-lookup"><span data-stu-id="08bac-140">Windows PowerShell® uses two sets of blank \<maml:para> tags to separate the command output from the command.</span></span>

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