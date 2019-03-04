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
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a>Hinzufügen von Beispielen zu einem Cmdlet-Hilfethema

- [Wichtige Informationen zu Beispielen, in der Cmdlet-Hilfe](#Things-to-Know-about-Examples-in-Cmdlet-Help)

- [Hilfeansichten, die Beispiele anzeigen](#Help-Views-that-Display-Examples)

- [Hinzufügen eines Knotens Beispiele](#Adding-an-Examples-Node)

- [Hinzufügen von vorhergehenden Zeichen](#Adding-Preceding-Characters)

- [Der Befehl hinzufügen](#Adding-the-Command)

- [Hinzufügen einer Beschreibung](#Adding-a-Description)

- [Beispiel der Ausgabe hinzufügen](#Adding-Example-Output)

## <a name="things-to-know-about-examples-in-cmdlet-help"></a>Wichtige Informationen zu Beispielen, in der Cmdlet-Hilfe

- Listen Sie alle Parameternamen in den Befehl aus, selbst wenn die Namen der Parameter optional sind. Dadurch wird den Benutzer den Befehl einfach zu interpretieren.

- Vermeiden Sie Aliase und partielle Parameternamen, obwohl sie in Windows PowerShell® funktionieren.

- In der Beschreibung zu Beispiel erläutert, die rationale für die Konstruktion des Befehls. Erläutern Sie, warum Sie bestimmte Parameter und Werte ausgewählt haben, und wie Sie Variablen verwenden.

- Wenn der Befehl Ausdrücke verwendet, wird diese im Detail erläutert.

- Wenn der Befehl verwendet die Eigenschaften und Methoden der Objekte, insbesondere die Eigenschaften, die nicht in der Standardanzeige angezeigt werden anhand des Beispiels, wie die Gelegenheit dem Benutzer mitgeteilt, über das Objekt.

## <a name="help-views-that-display-examples"></a>Hilfeansichten, die Beispiele anzeigen

Beispiele, die nur in den Ansichten "ausführlich" und "vollständig" der Cmdlet-Hilfe angezeigt werden.

## <a name="adding-an-examples-node"></a>Hinzufügen eines Knotens Beispiele

Das folgende XML zeigt, wie einen Beispielen-Knoten hinzugefügt, der einen einzelnen Beispiel-Knoten enthält. Fügen Sie zusätzliches Beispiel-Knoten für die einzelnen Beispiele, die Sie im Thema einschließen möchten.

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a>Einen Titel hinzufügen

Das folgende XML zeigt, wie Sie einen Titel für das Beispiel hinzufügen. Der Titel ist, legen Sie das Beispiel abgesehen von den anderen Beispielen verwendet. Windows PowerShell® verwendet einen Standardheader, der eine sequenzielle Beispielnummer enthält.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a>Hinzufügen von vorhergehenden Zeichen

Das folgende XML zeigt, wie Sie Zeichen, z. B. der Windows PowerShell-Eingabeaufforderung hinzufügen, die unmittelbar vor der Befehl im Beispiel (ohne Leerzeichen) angezeigt werden. Windows PowerShell® verwendet die Windows PowerShell-Eingabeaufforderung: C:\PS>.

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

## <a name="adding-the-command"></a>Der Befehl hinzufügen

Das folgende XML zeigt, wie den eigentlichen Befehl, der im Beispiel hinzugefügt wird. Wenn Sie den Befehl hinzufügen möchten, geben Sie den gesamten Namen (Alias nicht verwenden) des-Cmdlets und Parameter. Außerdem verwenden Sie Kleinbuchstaben, wann immer möglich.

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

## <a name="adding-a-description"></a>Hinzufügen einer Beschreibung

Das folgende XML zeigt, wie Sie eine Beschreibung für das Beispiel hinzufügen. Windows PowerShell® verwendet einen einzigen Satz von \<maml: para >-Tags für die Beschreibung, obwohl mehrere \<maml: para > Tags können verwendet werden.

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

## <a name="adding-example-output"></a>Beispiel der Ausgabe hinzufügen

Das folgende XML zeigt, wie Sie die Ausgabe des Befehls hinzufügen. Die Ergebnisse Befehlsinformationen ist optional, aber in einigen Fällen ist es hilfreich sein, den Effekt des anhand bestimmter Parameter veranschaulichen. Windows PowerShell® anhand von zwei Leerzeichen \<maml: para > Tags aus, um die Ausgabe des Befehls von dem Befehl zu trennen.

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